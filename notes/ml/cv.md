---
layout: default
title: ML CV
permalink: /notes/ml/cv/
---

# ML / CV

<div class="post-list">
{% for note in site.notes %}
  {% assign note_domain = note.domain | downcase | strip %}
  {% assign note_topic = note.topic | downcase | strip %}
  {% if note_domain == "ml" and note_topic == "cv" %}
<article class="post-preview">
  <a href="{{ note.url }}" class="post-preview-card" aria-label="Open note {{ note.title }}">
    <h3>{{ note.title }}</h3>
    {% if note.excerpt %}
    <p class="excerpt">{{ note.excerpt | strip_html | truncatewords: 30 }}</p>
    {% endif %}
  </a>
</article>
  {% endif %}
{% endfor %}
</div>
