---
layout: project
short_title: Visual Indexing for the Impresso Project
page_title: Bringing Visual Indexing to Millions of Press Images
banner: uploads/projects/impresso1/Summary.svg
---

In the beginning of 2019, I worked with the members of the [Impresso team](https://impresso-project.ch/) to bring simple visual search capabilities to their astounding collection of historical newspapers.

- Efficient computation of the visual signatures for the **scale of the project (Millions of images)**
- Integration of the search in the existing infrastructure through SOLR extensions, **allowing complex queries filtering on the metadata and ranking on the visual similarity** of an input image at the same time (year, article topic, etc.)
- External service allowing users to **search from their own images** and not just elements already indexed in the database
- Ability to search similar people in the data through the use of **face detection and face recognition**

- (bonus) Helping the team moving their expensive computation on a Kubernetes cluster in order to scale some of the very large processes they do. 