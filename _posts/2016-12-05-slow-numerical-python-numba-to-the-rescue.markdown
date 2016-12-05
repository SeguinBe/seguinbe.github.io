---
title: Slow numerical Python? Numba to the rescue!
layout: post
---

It is no secret that Python is a slow language, and that the only reason it is viable as a programming language for numerical computing is because of the low level implementation of the numerical routines (thanks `numpy` people).

However, it sometimes happen that it is not easy (or even impossible) to properly write your algorithm in numpy-compatible form. In such cases, when you need a lot of loops and conditions, it is very easy to lose yourself. Should I write some c/c++ and interface it to python (terrible idea)? Should I write some low level code in [Cython](http://cython.readthedocs.io/en/latest/index.html) (Cython is awesome but needs some work to set up at the beginning)? Should I wait for compatible JIT Python system like [Pyston](https://blog.pyston.org/) (I have high expectations for this project but it is way too early, and it does not even support Python3...)?

A possible solution might come from [Numba](http://numba.pydata.org/), a Numpy aware compiler for numerical-oriented Python code.

### The Algorithm

A relevant case happened to me when I was incorporating the simple and elegant image search algorithm based on integral images [published at ICLR 2016](https://arxiv.org/abs/1511.05879).

The basic idea is simple, you take a CNN feature map (for instance `pool5` of the VGG16 network). You have a feature map that is of shape $$ (N_{filters}, H, W)$$. Given a region, the descriptor is obtained by summing over the spatial dimensions of the feature map on that region, giving a $$N_{filters}$$ dimension vector, that can directly be compared.

{% highlight python %}
# Feature map
f.shape
# (512, 18, 16)
{% endhighlight %}

Making the integral image out of it is relatively easy :
{% highlight python %}
import numpy as np

def make_integral_image(feat_map):
    result = np.zeros((feat_map.shape[0], feat_map.shape[1] + 1, feat_map.shape[2] + 1), dtype=np.float64)
    result[:, 1:, 1:] = np.cumsum(np.cumsum(feat_map, axis=2), axis=1)
    return result

integral_image = make_integral_image(f)
integral_image.shape
# (512, 19, 17)
{% endhighlight %}

Then having a function giving back the normalized integral of a region is : 
{% highlight python %}
def get_feature_from_integral_image(integral_image, y1, x1, y2, x2):
    result = integral_image[:, y2, x2] + \
                integral_image[:, y1, x1] - \
                integral_image[:, y1, x2] - \
                integral_image[:, y2, x1]
    # Normalize the feature vector
    result /= np.sqrt(np.sum(result * result))
    return result
{% endhighlight %}
_Note : here, for simplicity, I just consider the sum of the region directly with the integral image. The original algorithm uses a variation allowing a max-pool approximation instead of a sum-pool._

Now, if you want to find the best matching region in your image given a query vector, relatively straight-forward indeed :
{% highlight python %}
def search_one_integral_image(integral_image, query_descriptor, query_ratio):
    best_score = np.inf
    for y2 in range(integral_image.shape[1]):
        for x2 in range(integral_image.shape[2]):
            for y1 in range(y2):
                for x1 in range(x2):
                	# Only evaluate windows with a similar ratio
                    if 0.8 < (y2 - y1) / (x2 - x1) / query_ratio < 1.2:
                        tmp_descriptor = get_feature_from_integral_image(integral_image, y1, x1, y2, x2)
                        score_tmp = np.sqrt(
                            np.sum((tmp_descriptor - query_descriptor) * (tmp_descriptor - query_descriptor)))
                        if score_tmp < best_score:
                            best_score = score_tmp
                            best_position = (y1, x1, y2, x2)
    return best_score, best_position
{% endhighlight %}
_Note : again, this is a huge simplification of the original algorithm which uses a branching algorithm to avoid evaluating all possible windows like we are doing here._

### Numba magic

So the previous implementation is not slow, but definitely limiting if you want to evaluate many potential images against your query vector. Taking roughly **90ms**. But here comes the Numba magic, just adding a function annotation telling it to be compiled brings the timing to **61.5ms** already.

{% highlight python %}
import numba
@numba.jit(nopython=True, nogil=True)
def get_feature_from_integral_image(integral_image, y1, x1, y2, x2):
	...
{% endhighlight %}

And then, adding the same decoration to the `search_one_integral_image` will bring it to **16ms**, more than **5X faster with two lines**!!

Additionally, the call to the function `search_one_integral_image` now releases the Global Interpreter Lock, which allows for easier parallelism. For instance, the following code will actually be able to naturally use more than 1 CPU which is sometimes a challenge in numerical-heavy python :

{% highlight python %}
with ThreadPoolExecutor(max_workers=20) as e:
	<code using search_one_integral_image>
{% endhighlight %}

All in all, if you have never used Numba, give it a try, it does not solve everything but can be every practical in many situations.
