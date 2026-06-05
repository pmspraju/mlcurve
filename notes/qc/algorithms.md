---
layout: default
title: QC Algorithms
permalink: /notes/qc/algorithms/
---

# QC / Algorithms

<div class="post-list">
{% for note in site.notes %}
  {% assign note_domain = note.domain | downcase | strip %}
  {% assign note_topic = note.topic | downcase | strip %}
  {% if note_domain == "qc" and note_topic == "algorithms" %}
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
