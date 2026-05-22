---
layout: default
title: Blog
permalink: /blog/
---

# All Posts

{% for post in site.posts %}
<article class="post-preview">
    <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
    <p class="post-meta">
        {{ post.date | date: "%B %d, %Y" }}
        {% if post.source %}• {{ post.source }}{% endif %}
    </p>
    {% if post.excerpt %}
    <p class="excerpt">{{ post.excerpt | strip_html | truncatewords: 50 }}</p>
    {% endif %}
    <a href="{{ post.url }}" class="read-more">Read more →</a>
</article>
<hr>
{% endfor %}