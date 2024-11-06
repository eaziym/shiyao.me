---
layout: default
title: Projects
permalink: /projects/
---

# Projects

{% assign filtered_projects = site.projects | where_exp: "project", "project.title != 'Projects'" %}
{% for project in filtered_projects %}

<div class="project-preview">
  <div class="project-image">
    {% if project.cover_image %}
    <img src="{{ project.cover_image | relative_url }}" alt="{{ project.title }}">
    {% endif %}
  </div>
  <div class="project-content">
    <h2><a href="{{ project.url | relative_url }}">{{ project.title }}</a></h2>
    <div class="tags">
      {% for tag in project.tags %}
        <span class="tag">{{ tag }}</span>
      {% endfor %}
    </div>
    <p>{{ project.problem }}</p>
    <a href="{{ project.url | relative_url }}" class="read-more">Read More →</a>
  </div>
</div>
{% endfor %}
