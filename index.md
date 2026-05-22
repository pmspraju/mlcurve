---
layout: default
title: Home
---

# Welcome to MLCurve

**Visualizing Machine Learning, One Curve at a Time**

MLCurve is your resource for understanding machine learning through clear visualizations, curated insights, and in-depth analysis.

## Latest Posts

<div class="post-list">
{% for post in site.posts limit:5 %}
<article class="post-preview">
    <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
    <p class="post-meta">{{ post.date | date: "%B %d, %Y" }} • {{ post.source }}</p>
    {% if post.excerpt %}
    <p class="excerpt">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
    {% endif %}
    <a href="{{ post.url }}" class="read-more">Read more →</a>
</article>
{% endfor %}
</div>

[View All Posts →](/blog/)

---

## What We Cover

<div class="topics-grid">
    <div class="topic">
        <h3>📊 Learning Curves</h3>
        <p>Understanding model training dynamics</p>
    </div>
    <div class="topic">
        <h3>🤖 AI Research</h3>
        <p>Latest papers and breakthroughs</p>
    </div>
    <div class="topic">
        <h3>📈 Model Analysis</h3>
        <p>Deep dives into architectures</p>
    </div>
    <div class="topic">
        <h3>🔬 Experiments</h3>
        <p>Practical ML tutorials</p>
    </div>
</div>