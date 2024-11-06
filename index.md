---
layout: default
title: Home
profile_image: /assets/images/me.jpeg
---

<div class="profile-header">
  <img src="{{ '/assets/images/me.jpeg' | relative_url }}" alt="Shiyao Meng" class="profile-image">
  <div class="profile-content">
    <h1>Hi, I'm Shiyao 👋</h1>

    <p>I'm a curious problem solver who leverages AI and automation to create impactful solutions. With a background in both technology and business, I enjoy tackling real-world inefficiencies through innovative approaches.</p>

  </div>
</div>

## What I Do

- 🤖 Build AI-powered automation solutions
- 🛠️ Develop tools that solve practical problems
- 🌱 Grow communities and share knowledge

## Featured Projects

{% if site.projects and site.projects.size > 0 %}
{% assign featured_projects = site.projects | sort: 'date' | reverse | limit: 3 %}
{% for project in featured_projects %}

<div class="project-preview">
<div class="project-image">
{% if project.cover_image %}
<img src="{{ project.cover_image | relative_url }}" alt="{{ project.title }}">
{% endif %}
</div>
<div class="project-content">
<h2><a href="{{ project.url | relative_url }}">{{ project.title }}</a></h2>
<p>{{ project.problem }}</p>
<div class="metrics-preview">
{% for metric in project.metrics limit: 2 %}
<div class="metric">
<span class="value">{{ metric.value }}</span>
<span class="label">{{ metric.label }}</span>
</div>
{% endfor %}
</div>
</div>
</div>
{% endfor %}
{% else %}

  <p>No projects available at the moment.</p>
{% endif %}
