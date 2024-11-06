---
layout: default
title: Projects
permalink: /shiyao.me/projects/
---

# Projects

{% for project in site.projects %}

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
