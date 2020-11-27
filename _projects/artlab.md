---
layout: project
short_title: Artlab Installation
page_title: ArtLab Installation, or How to Generate a Time-Oriented Visual Space from Folders of Photographs
banner: uploads/projects/artlab/installation_2.jpg
---

<figure>
<video width="80%" controls autoplay class="center-image">
  <source src="{{ site.baseurl }}/uploads/projects/artlab/demo.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>
<center>Screen capture of the touch-screen interface.</center>
</figure>

For the _50th Anniversary of EPFL_, there was [an exhibition](https://www.epfl.ch/campus/art-culture/museum-exhibitions/artlab/infinity-room-2-2/) (actually [two](https://www.epfl.ch/campus/art-culture/museum-exhibitions/artlab/current-exhibitions/infinity-room-i/)) at the ArtLab museum celebrating the campus and its history.

For this occasion, I was asked by [Prof. Sarah Kenderdine](https://sarahkenderdine.info/bio-and-cv) to leverage the photographic archive of the school. The initial idea was to digitize all the physical negatives as well as use the born-digital material, the shift happening around the year 2003. This meant I had to find a way to provide visualisations for hundreds of thousands of mostly poorly labelled material.

In practice, I was given access to the work folder of the EPFL photographer Alain Herzog. Since it was not meant to be an actual information system, I could not expect a trusty labelled. In the end, I had the following data:

- List of folders by year.
- Inside each year-folder, a non-consistent folder and image-file organization. Folder names being roughly indicative to the corresponding event.

Given the tight deadlines I had to work with, a proper labelling work was out of the question. Also showing 300'000 random photographs is not a very interesting experience, especially since many of them are from social events, and are then uninteresting without additiional context.

What I managed to do was a mix of automatic tagging and event tagging:

- Computer vision was used to detect certain visual semantic classes (architecture, portrait, etc.)
- A simple exploration interface was used to select the folders of reoccuring events through the years (diploma ceremony, sport events, etc.)

This brought us the possibility to split the large collection of images in coherent chunks which would be more interesting to navigate across time and visual similarity. A new algorithm allowing to **position images based on visual similarity _AND_ the corresponding year of the image** was implemented, allowing the users exploring the evolution of events, portraits' fashion, or building construction through the history of the school.

The generated visualisations were then exported to an amazing museology experience implemented by [Nikolaus Völzow](https://voelzow.de/), which was using both a touch-screen interface as an iPad and a large video-projector to either mirror the complex visualisations or to bring a zoomed-version of a singled-out photograph.

The main issue was that the digitization part (physical negatives, pre-2003), in the end produced only a tiny portion compared to the mass of images available post-2003. Even by using clever sampling tricks to try to alleviate this problem, it stays extremely visible in the end visualisations where certain years are packed while there are gaps of 10 years without available data. However, given the fact that the whole project was achieved in only few weeks, I would still consider it a success.

![Installation]({{ site.baseurl }}/uploads/projects/artlab/installation.jpg){: .center-image width="80%"}
<figcaption markdown="1">
The final installation.
</figcaption>

<iframe width="100%" height="500px"
    src="https://www.youtube.com/embed/4vWaYj26WsQ">
</iframe>
