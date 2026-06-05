---
layout: default
title: Blog
permalink: /blog/
---

# All Posts

{% for post in site.posts %}
<article class="post-preview">
    <a href="{{ post.url }}" class="post-preview-card" aria-label="Open post {{ post.title }}">
        <h2>{{ post.title }}</h2>
        <p class="post-meta">
            {{ post.date | date: "%B %d, %Y" }}
            {% if post.source %}• {{ post.source }}{% endif %}
        </p>
        {% if post.excerpt %}
        <p class="excerpt">{{ post.excerpt | strip_html | truncatewords: 50 }}</p>
        {% endif %}
    </a>
</article>
{% endfor %}