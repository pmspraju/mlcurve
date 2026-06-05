---
layout: default
title: ML Notes
permalink: /notes/ml/
---

# ML Notes

<div class="post-list">
{% assign ml_notes = site.notes | where: "domain", "ml" | sort: "title" %}
{% for note in ml_notes %}
<article class="post-preview">
    <a href="{{ note.url }}" class="post-preview-card" aria-label="Open note {{ note.title }}">
        <h3>{{ note.title }}</h3>
        {% if note.topic %}
        <p class="post-meta">{{ note.topic }}</p>
        {% endif %}
        {% if note.excerpt %}
        <p class="excerpt">{{ note.excerpt | strip_html | truncatewords: 30 }}</p>
        {% endif %}
    </a>
</article>
{% endfor %}
</div>
