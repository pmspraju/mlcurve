---
layout: default
title: Latest
---

{% assign latest = site.posts.first %}

{% if latest %}
<article class="post">
    <header class="post-header">
        <h1 class="post-title">{{ latest.title }}</h1>
        <div class="post-meta">
            <time datetime="{{ latest.date | date_to_xmlschema }}">
                {{ latest.date | date: "%B %d, %Y" }}
            </time>
            {% if latest.source %}
            <span class="separator">•</span>
            <span>{{ latest.source }}</span>
            {% endif %}
            <span class="separator">•</span>
            <a class="meta-back-link" href="/blog/" aria-label="Back to posts list">
                <span aria-hidden="true">&#x21A9;</span>
            </a>
        </div>
    </header>

    <div class="post-content">
        {{ latest.content }}
    </div>

    <footer class="post-footer">
        {% if latest.source_url %}
        <p>Source: <a href="{{ latest.source_url }}" target="_blank">{{ latest.source }}</a></p>
        {% endif %}
    </footer>
</article>

<div class="post-navigation">
    {% if latest.next.url %}
    <a href="{{ latest.next.url }}" class="prev-post" title="Older posts"><-</a>
    {% endif %}

    <a href="/blog/" class="next-post" title="Blog archive">-></a>
</div>
{% else %}
# No Posts Yet

Add your first file in `_posts` using `YYYY-MM-DD-title.md` and it will appear here.
{% endif %}