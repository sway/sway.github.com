---
layout: page
title: my egoistic
tagline: my life on github
---

{% if site.posts.size > 0 %}
{% for post in site.posts %}
{% if forloop.first %} 
<span class="label success">Latest post</span>

## [{{ post.title }}][title]

{{ post.content }}

[title]:{{ BASE_PATH }}{{ post.url }}

{% if site.posts | size > 1 %}
<h2>Older posts</h2>
<ul>
{% endif %}

{% else %}
<li><span class="label notice">{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
{% endif %}
{% endfor %}
{% if site.posts | size > 1 %}
</ul>
{% endif %}
{% endif %}
