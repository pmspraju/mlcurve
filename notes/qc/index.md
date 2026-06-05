---
layout: default
title: QC Notes
permalink: /notes/qc/
---

# QC Notes

<div class="post-list">
{% assign qc_notes = site.notes | where: "domain", "qc" | sort: "title" %}
{% for note in qc_notes %}
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
