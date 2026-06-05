---
layout: default
title: Notes
permalink: /notes/
---

# Notes

Choose a domain to browse focused notes and references.

<div class="post-list">
<article class="post-preview">
    <a href="/notes/ml/" class="post-preview-card" aria-label="Browse ML notes">
        <h3>ML</h3>
        <p class="excerpt">Machine learning notes across foundations, computer vision, transformers, optimization, and more.</p>
    </a>
</article>

<article class="post-preview">
    <a href="/notes/qc/" class="post-preview-card" aria-label="Browse QC notes">
        <h3>QC</h3>
        <p class="excerpt">Quantum computing notes across qubits, gates, algorithms, and practical intuition.</p>
    </a>
</article>
</div>

## All Notes

<div class="post-list">
{% assign sorted_notes = site.notes | sort: "title" %}
{% for note in sorted_notes %}
<article class="post-preview">
    <a href="{{ note.url }}" class="post-preview-card" aria-label="Open note {{ note.title }}">
        <h3>{{ note.title }}</h3>
        <p class="post-meta">{{ note.domain | upcase }} • {{ note.topic }}</p>
        {% if note.excerpt %}
        <p class="excerpt">{{ note.excerpt | strip_html | truncatewords: 30 }}</p>
        {% endif %}
    </a>
</article>
{% endfor %}
</div>
