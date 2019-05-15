---
layout: page
title: Past Projects
permalink: /projects/
order: 3
---

### Bringing Visual Search to the Impresso Project

In the beginning of 2019, I worked with the members of the [Impresso team](https://impresso-project.ch/) to bring simple visual search capabilities to their astounding collection of historical newspapers.

- Efficient computation of the visual signatures for the **scale of the project (Millions of images)**
- Integration of the search in the existing infrastructure through SOLR extensions, **allowing complex queries filtering on the metadata and ranking on the visual similarity** of an input image at the same time (year, article topic, etc.)
- External service allowing users to **search from their own images** and not just elements already indexed in the database
- Ability to search similar people in the data through the use of **face detection and face recognition**

- (bonus) Helping the team moving their expensive computation on a Kubernetes cluster in order to scale some of the very large processes they do. 

### Deliverables at DHLAB, EPFL

Expanded information to be added soon for each subproject. Complete information can always be found in the manuscript of my [PhD thesis](https://infoscience.epfl.ch/record/261212)

- Spearheaded the developement of [**dhSegment**](https://github.com/dhlab-epfl/dhSegment) (originally created for parsing the documents of the Foundazione Cini, the main data for my PhD). As a generic document processing pipeline dhSegment is **now widely used for the Venice Time Machine project**, and by many Universities around the world.
- **Complete semi-automatic parsing of the 340'000 documents** of the photo-archive of the Cini foundation (separation visual elements, OCR recognition, metadata assignment, partial Linked-Open-Data linking, ...)
- Global visual analyzing of the Cini photo-archive, **automatically discovering conflicting attributions for more than 1'600 artworks**, conflicts that were unknown to archivists.
- Completely built the **first visual search engine for exploring the propagation of "form" in the Visual Arts**, leveraging the power of Convolutional Neural Networks. The system was continuously trained through feedback from users to reach impressive performance. Most of the interface, and the exact same backend is now powering the visual search capabilities of the [Diamond platform of the Time Machine project (section Images)](https://diamond.timemachine.eu/).
