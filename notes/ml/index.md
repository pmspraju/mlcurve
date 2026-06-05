---
layout: default
title: ML Notes
permalink: /notes/ml/
---

# ML Notes

{% assign topic_keys = "" | split: "" %}
{% for note in site.notes %}
    {% assign note_domain = note.domain | downcase | strip %}
    {% assign note_topic = note.topic | downcase | strip %}
    {% if note_domain == "ml" and note_topic != "" %}
        {% unless topic_keys contains note_topic %}
            {% assign topic_keys = topic_keys | push: note_topic %}
        {% endunless %}
    {% endif %}
{% endfor %}

{% assign topic_keys = topic_keys | sort %}

{% if topic_keys.size > 0 %}
{% for topic in topic_keys %}
<h2>{{ topic | replace: "-", " " | capitalize }}</h2>
<div class="post-list">
{% for note in site.notes %}
    {% assign note_domain = note.domain | downcase | strip %}
    {% assign note_topic = note.topic | downcase | strip %}
    {% if note_domain == "ml" and note_topic == topic %}
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
{% endfor %}
{% else %}
<p>No ML topics found yet.</p>
{% endif %}
