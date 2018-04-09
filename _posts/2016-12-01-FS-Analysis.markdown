---
title: Figure Skating Data Analysis
layout: post
---


_I am just starting this website and thought that this tinkering I did recently was a very nice vehicle to experiment with this blogging system, this post is not representative of what I will be posting about in the future._

So the people who know me well probably know that despite having almost never skated myself, I have a weird fixation with Figure Skating competitions. And recently on the [Golden Skate Forum](http://www.goldenskate.com/forum), the user *Geek on Ice* started making very insightful analysis (like [this](http://www.goldenskate.com/forum/showthread.php?61466-2016-Cup-of-China-Data-Analysis-Men)) from the very precise protocol sheets (like [this one](http://www.isuresults.com/results/season1617/gpjpn2016/gpjpn2016_Men_SP_Scores.pdf)) which are now used for scoring Figure Skating competitions.

I naturally thought that this was a brilliant idea and decided it would be fun to try to go a bit larger scale than just the analysis of one competition. So I started a Jupyter iPython Notebook and started trying things.

**TL-DR:** In the end, In the end, the method allows **complete automatic extraction** of the information in the protocol sheets. It takes roughly one minute per file on my laptop (which is honestly quite slow). Also, until some bug is solved, it only works for current season files.

Below is a visualisation of the Men Free-Skate scores of this Grand Prix season. You can look at the correlation or variation of two quantities of your choice. You can also filter per competition.

By default, the PCS/TES plot is a way to see the more artistic skaters (like Kolyada or Brown) compared to the more technical (like Jin). Though, it seems that if you are high enough technically, you will always get some good PCS anyway...

Another interesting combination is Base-Value/TES, it shows how some skaters go for difficult elements and how some others get more out of their jumps with high GoE.

The complete extraction for the Men Grand Prix Events of 2016 is available [here](https://dl.dropboxusercontent.com/u/14341018/GP_2016_Men.zip)

The rest of this post is more for people interested in how this was created.

# Extraction Process

## Gathering the files

The first thing to do was to download all the protocol sheets from the previous competitions. Unfortunately the ISU (_International Skating Union_, in charge of judging the competitions) does not have the best organized website.

### Indexing the competitions

They have a different page per competition, but I was not able to find any index page indexing all the competitions.

Anyway, since they often use very similar patterns for the URLs, it is possible to generate them automatically. The only pitfall comes from the fact that they changed year numerotation in 2010, and started using folders in 2015.

The corresponding code is :
{% highlight python %}
base_competitions = ['gpusa%sy', 'gpcan%sy', 'gpfra%sy', 'gprus%sy', 'gpchn%sy', 'gpjpn%sy',  'gpf%yy', 'ec%ny', 'fc%ny', 'wc%ny']

def convert_base(b, season_start_year):
    if season_start_year < 2010:
        sy, ny = str(season_start_year)[-2:], str(season_start_year+1)
    else:
        sy, ny = str(season_start_year), str(season_start_year+1)
    yy = sy[-2:] + ny[-2:]
    return b.replace('%sy', sy).replace('%ny', ny).replace('%yy', yy)

def make_competition_urls_for_season(season_start_year):
    sy, ny = str(season_start_year)[-2:], str(season_start_year+1)
    yy = sy[-2:] + ny[-2:]
    if season_start_year < 2015:
        base_url = "http://www.isuresults.com/results/"
    else:
        base_url = "http://www.isuresults.com/results/season{}/".format(yy)
    return [base_url+convert_base(b, season_start_year) for b in base_competitions]
{% endhighlight %}

That way for instance, the URLs for 2009-2010 are :

{% highlight python %}
['http://www.isuresults.com/results/gpusa09',
'http://www.isuresults.com/results/gpcan09',
'http://www.isuresults.com/results/gpfra09',
'http://www.isuresults.com/results/gprus09',
'http://www.isuresults.com/results/gpchn09',
'http://www.isuresults.com/results/gpjpn09',
'http://www.isuresults.com/results/gpf0910',
'http://www.isuresults.com/results/ec2010',
'http://www.isuresults.com/results/fc2010',
'http://www.isuresults.com/results/wc2010']
{% endhighlight %}

But the result for the season 2015-2016 is :
{% highlight python %}
['http://www.isuresults.com/results/season1516/gpusa2015',
'http://www.isuresults.com/results/season1516/gpcan2015',
'http://www.isuresults.com/results/season1516/gpfra2015',
'http://www.isuresults.com/results/season1516/gprus2015',
'http://www.isuresults.com/results/season1516/gpchn2015',
'http://www.isuresults.com/results/season1516/gpjpn2015',
'http://www.isuresults.com/results/season1516/gpf1516',
'http://www.isuresults.com/results/season1516/ec2016',
'http://www.isuresults.com/results/season1516/fc2016',
'http://www.isuresults.com/results/season1516/wc2016']
{% endhighlight %}

### Downloading the separate files for each competition

Each competition webpage (like [this one](http://www.isuresults.com/results/season1617/gpjpn2016/) being made of several events, each having a separate protocol sheet, it is necessary to parse the webpage to gather everything. Fortunately that is relatively easy :

{% highlight python %}
import shutil
from lxml import html
import requests

def download_files(base_url, filenames, output_dir):
    """Download the list of files referenced from base_url and save them in output_dir"""
    for filename in filenames:
        url = base_url + '/' + filename
        print('Downloading {}'.format(url))
        response = requests.get(url, stream=True)
        with open(os.path.join(output_dir, filename), 'wb') as out_file:
            shutil.copyfileobj(response.raw, out_file)
        del response
        
def get_sheet_links(url):
    """Get all the protocol sheets url referenced from a competition page"""
    r = requests.get(url)
    assert r.status_code == 200, url
    # Parse html content
    page = html.fromstring(r.content)
    # Get all the links in the page
    all_links = page.xpath('//a/@href')
    # Filter only the links which direct to a protocol file
    return [l for l in all_links if '_Scores.pdf' in l] + [l for l in all_links if '_scores.pdf' in l]
{% endhighlight %}

Thanks to this, I was able to download all the protocols since the inception of the new judging system in the season 2004-2005. A quick `ls -lR | grep .pdf | wc -l` tells me that **I actually downloaded 1144 protocol files**. Not sure how many marks it represents but assuming 9 judges and 12 conccurents per event, basically in the order of **125'000+**.

## Reading the files

### Reading tables

Now comes the complicated part, parsing them... Reading PDF files is notoriously complex because they are only made for display and not for editing or analysis. Fortunately I came upon a tool called [tabula](http://tabula.technology/), which allow the extraction of tables in PDF files. It comes with a very nice web application in order to select the areas of the files you are interested in.

![tabula]({{ site.baseurl }}/uploads/fs_analysis_data/tabula.png)

By selecting the separate tables like in the above picture, you almost get the result you would like to get right away. There is one issue if no element has remark (like '<', '*' or 'e' for the edge calls or under-rotations), tabula does not create the corresponding at all. Similarly it might some times merge the 'Base Value' column with the 'After second half' one. Fortunately, both these issues can be corrected programmatically.

### Finding the position of the tables

In order to avoid using the web interface to manually select the tables for each skater, I thought it should be possible to find about their position automatically. For this I used the `pdfminer` python package, which allows delving into a pdf file.

As I said previously, pdf files are a nightmare to work with, they basically are a list of boxes with text inside, with no organisation at all. My guess however was that using correct words to look for would be enough to predict where the different tables that need to be extracted are.

Surprisingly, it worked! Using `'Executed Elements'` in order to find the separation between the skater header and the TES table, `'Program Components'` to separate between the TES table and the PCS table and `'Deductions'` to find out when the PCS table ends, it is possible to compute the ranges of the tables that we need to extract. :-)

_Because the code is a bit messy here, I do not display it, I will probably share it on github eventually_

### The desillusion...

This works great... on the current season file.

The reason is not because of the trick of looking for key words to extract the table positions, I was careful enough to make it work for all the 1'100+ files I had. But it comes from a bug in tabula (or actually from PDFBox apparently which is a library used by tabula). I [reported it on their github](https://github.com/tabulapdf/tabula-java/issues/126) but until it is corrected or I find a way around, it is a bit complicated to extract previous years...

## Parsing the tables

From the tables, it is relatively easy to gather all the information in JSON files. Below is the final description of one skater in one event :

{% highlight json %}
    {
        "elements": [
            {
                "goe": -4.0,
                "bv": 10.3,
                "label": "4T",
                "panel": [
                    -3.0, -3.0, -3.0, -3.0, -3.0, -3.0, -3.0, -3.0, -3.0
                ],
                "total": 6.3,
                "info": "",
                "second_half": false
            },
            {
                "goe": 1.14,
                "bv": 14.8,
                "label": "4S+3T",
                "panel": [
                    2.0, 1.0, 1.0, 1.0, 1.0, 1.0, 0.0, 1.0, 2.0
                ],
                "total": 15.94,
                "info": "",
                "second_half": false
            },
            ...
        ],
        "deductions": 1.0,
        "rank": 1,
        "components": {
            "TR": {
                "full_label": "Transitions",
                "factor": 1.0,
                "panel": [
                    8.75, 8.75, 9.0, 9.5, 9.25, 9.25, 9.0, 9.0, 9.25
                ],
                "average": 9.07
            },
            "PE": {
                "full_label": "Performance",
                "factor": 1.0,
                "panel": [
                    8.75, 9.0, 9.25, 9.0, 9.0, 9.25, 9.0, 8.75, 9.0
                ],
                "average": 9.0
            },
            ...
        },
        "total_bv": 47.75,
        "TES": 51.68,
        "total_score": 96.57,
        "total_goe": 3.93,
        "nation": "ESP",
        "PCS": 45.89,
        "starting_number": 6,
        "name": "Javier FERNANDEZ"
    }
{% endhighlight %}



