---
layout: page
title: Journal
permalink: journal
---

<div class="posts">
  {% for post in site.categories.journal %}
    <strong><time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date: "%A, %B %d, %Y" }}</time></strong>
    {{ post.content }}
  {% endfor %}
</div>