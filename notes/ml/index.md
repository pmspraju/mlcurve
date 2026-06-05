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

## Topics

{% if topic_keys.size > 0 %}
<div class="post-list">
{% for topic in topic_keys %}
<article class="post-preview">
    <a href="#topic-{{ topic | slugify }}" class="post-preview-card" aria-label="Open topic {{ topic | replace: '-', ' ' | capitalize }}">
        <h3>{{ topic | replace: "-", " " | capitalize }}</h3>
    </a>
</article>
{% endfor %}
</div>
{% else %}
<p>No ML notes yet. Add files under <code>_notes/ml/</code> with a <code>topic</code> value.</p>
{% endif %}

## Notes By Topic

{% for topic in topic_keys %}
<h2 id="topic-{{ topic | slugify }}">{{ topic | replace: "-", " " | capitalize }}</h2>
<div class="post-list">
{% assign found = false %}
{% for note in site.notes %}
    {% assign note_domain = note.domain | downcase | strip %}
    {% assign note_topic = note.topic | downcase | strip %}
    {% if note_domain == "ml" and note_topic == topic %}
        {% assign found = true %}
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
{% unless found %}
<p>No notes yet in this topic.</p>
{% endunless %}
</div>
{% endfor %}
