---
layout: single
title: "Research Projects"
permalink: /research-projects/
author_profile: true
---

<div class="research-projects-intro">
  <p>
    This page provides a concise overview of my ongoing and completed research projects in biostatistics,
    clinical data science, and applied statistical modeling. Each project card links to a dedicated page
    where a fuller methods/results write-up will be added.
  </p>
</div>

<div class="research-grid">
  {% assign projects = site.research-projects | sort: "last_modified_date" | reverse %}
  {% for post in projects %}
    <article class="research-card research-project-item">
      <div class="content-card__header">
        <h2 class="content-card__title">
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </h2>
        <p class="content-card__meta research-project-meta">
          {% if post.venue %}
            <span class="research-meta-chip">{{ post.venue }}</span>
          {% endif %}
          {% if post.period %}
            <span class="research-meta-chip">{{ post.period }}</span>
          {% endif %}
          {% if post.status %}
            <span class="research-meta-chip research-meta-chip--status">{{ post.status }}</span>
          {% endif %}
        </p>
      </div>

      <div class="content-card__body">
        <p>{{ post.summary | default: post.excerpt | strip_html | strip }}</p>
      </div>

      <div class="research-card__footer">
        <a class="btn btn--primary btn--small" href="{{ post.url | relative_url }}">View project</a>
      </div>
    </article>
  {% endfor %}
</div>
