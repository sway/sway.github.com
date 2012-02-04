---
layout: page
title: my egoistic
tagline: my life on github
---

{% if site.posts.size > 0 %}
{% for post in site.posts %}
{% if forloop.first %} 
<article >
<span class="label date">{{ post.date | date_to_string }}</span>

<h2><a href="{{BASE_PATH}}{{ post.url }}">{{ post.title }}</a></h2>

{{ post.content }}

</article>
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
