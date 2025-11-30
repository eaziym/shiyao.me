---
layout: default
title: Home
profile_image: /assets/images/hi.png
---

<div class="profile-header">
  <img src="{{ '/assets/images/hi.png' | relative_url }}" alt="Shiyao Meng" class="profile-image">
  <div class="profile-content">
    <h1>Hi, I'm Shiyao</h1>

    <p>I'm a Technology & Analytics Associate at PKF-CAP LLP, building self-service analytics platforms and workflow automation systems. I specialize in creating AI-powered solutions that streamline operations and enable data-driven decision making. With a background spanning software engineering, data analytics, and business, I turn complex technical challenges into elegant, user-friendly solutions.</p>

  </div>
</div>

## What I Do

- Build self-service analytics platforms with RBAC and automated workflows
- Develop AI-powered automation systems (LLM agents, RAG, n8n workflows)
- Create full-stack web applications (Next.js, React, Flask, Python)
- Integrate real-time data pipelines and business intelligence dashboards
- Design workflow automation that reduces operational lifecycles by 70%+

## Featured Projects

{% if site.projects and site.projects.size > 0 %}
{% assign filtered_projects = site.projects | where_exp: "project", "project.title != 'Projects'" %}
{% assign featured_projects = filtered_projects | sort: 'date' | reverse | limit: 3 %}
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
