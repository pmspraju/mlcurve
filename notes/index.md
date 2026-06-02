---
layout: default
title: Notes
permalink: /notes/
---

# Notes

Choose a domain to browse focused notes and references.

<div class="post-list">
<article class="post-preview">
    <h3><a href="/notes/ml/">ML</a></h3>
    <p class="excerpt">Machine learning notes across foundations, computer vision, transformers, optimization, and more.</p>
    <a href="/notes/ml/" class="read-more">Browse ML notes →</a>
</article>

<article class="post-preview">
    <h3><a href="/notes/qc/">QC</a></h3>
    <p class="excerpt">Quantum computing notes across qubits, gates, algorithms, and practical intuition.</p>
    <a href="/notes/qc/" class="read-more">Browse QC notes →</a>
</article>
</div>

## All Notes

<div class="post-list">
{% assign sorted_notes = site.notes | sort: "title" %}
{% for note in sorted_notes %}
<article class="post-preview">
    <h3><a href="{{ note.url }}">{{ note.title }}</a></h3>
    <p class="post-meta">{{ note.domain | upcase }} • {{ note.topic }}</p>
    {% if note.excerpt %}
    <p class="excerpt">{{ note.excerpt | strip_html | truncatewords: 30 }}</p>
    {% endif %}
    <a href="{{ note.url }}" class="read-more">Open note →</a>
</article>
{% endfor %}
</div>
