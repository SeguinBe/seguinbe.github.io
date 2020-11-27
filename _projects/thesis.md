---
layout: project
page_title: Making Art Historical Photo Archives Searchable - From the Physical Archive to the Digitized Archive
short_title: Making large art historical photo archives searchable (PhD Thesis Output)
banner: uploads/publications/thesis_thumbnail.png
---

Expanded information to be added soon for each subproject. Complete information can always be found in the manuscript of my [PhD thesis](https://infoscience.epfl.ch/record/261212)

- Spearheaded the developement of [**dhSegment**](https://github.com/dhlab-epfl/dhSegment) (originally created for parsing the documents of the Foundazione Cini, the main data for my PhD). As a generic document processing pipeline dhSegment is **now widely used for the Venice Time Machine project**, and by many Universities around the world.
- **Complete semi-automatic parsing of the 340'000 documents** of the photo-archive of the Cini foundation (separation visual elements, OCR recognition, metadata assignment, partial Linked-Open-Data linking, ...)
- Global visual analyzing of the Cini photo-archive, **automatically discovering conflicting attributions for more than 1'600 artworks**, conflicts that were unknown to archivists.
- Completely built the **first visual search engine for exploring the propagation of "form" in the Visual Arts**, leveraging the power of Convolutional Neural Networks. The system was continuously trained through feedback from users to reach impressive performance. Most of the interface, and the exact same backend is now powering the visual search capabilities of the [Diamond platform of the Time Machine project (section Images)](https://diamond.timemachine.eu/).

## Final Interface Examples: exploring 380'000 images

### Exploring the visual space of Madonnas attributed to Bellini

<figure>
<video width="100%" controls class="center-image">
  <source src="{{ site.baseurl }}/uploads/projects/thesis/embedding.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>
<center>Exploring the 297 artworks (out of 649 images, duplicates automatically hidden) corresponding to the query <em>"Bellini Madonna"</em>. We can notice how the learned visual similarity help organize the visual space in a meaningful way.</center>
</figure>

### Searching Visually the Complete Collection

<figure>
<video width="100%" controls class="center-image">
  <source src="{{ site.baseurl }}/uploads/projects/thesis/visual_search.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>
<center>Searching purely visually (without relying on metadata), based on one image selected from the previous visualisation. It direclty brings us relevant images with matching patterns even when there is no matching metadata.</center>
</figure>
