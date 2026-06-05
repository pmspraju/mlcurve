---
layout: default
title: QC Notes
permalink: /notes/qc/
---

# QC Notes

<p class="breadcrumbs"><a href="/notes/">Notes</a> <span class="separator">/</span> <span>QC</span></p>

{% assign topic_keys = "" | split: "" %}
{% for note in site.notes %}
    {% assign note_domain = note.domain | downcase | strip %}
    {% assign note_topic = note.topic | downcase | strip %}
    {% if note_domain == "qc" and note_topic != "" %}
        {% unless topic_keys contains note_topic %}
            {% assign topic_keys = topic_keys | push: note_topic %}
        {% endunless %}
    {% endif %}
{% endfor %}

{% assign topic_keys = topic_keys | sort %}

<div class="post-list">
{% for topic in topic_keys %}
    {% assign article_count = 0 %}
    {% for note in site.notes %}
        {% assign note_domain = note.domain | downcase | strip %}
        {% assign note_topic = note.topic | downcase | strip %}
        {% if note_domain == "qc" and note_topic == topic %}
            {% assign article_count = article_count | plus: 1 %}
        {% endif %}
    {% endfor %}
<article class="post-preview">
    <a href="/notes/qc/{{ topic | slugify }}/" class="post-preview-card" aria-label="Open topic {{ topic | replace: '-', ' ' | capitalize }}">
        <h3>{{ topic | replace: "-", " " | capitalize }}</h3>
        <p class="post-meta">{{ article_count }} article{% if article_count != 1 %}s{% endif %}</p>
    </a>
</article>
{% endfor %}
</div>
