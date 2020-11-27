---
layout: page
title: Projects
permalink: /projects/
order: 3
---

{% for project in site.projects %}
<div>
  <a class="post-link" href="{{ project.url | relative_url }}">
  <h3>
    <strong>{{ project.short_title | escape }}</strong>
  </h3>
  <img class="center-image" src="{{project.banner | relative_url}}" style="width:100%;"/>
  </a>
  <hr/>
  <br/>
</div>
{% endfor %}
