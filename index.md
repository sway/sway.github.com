---
layout: default
title: Honza Ustohal
---

# honza ustohal


recent graduate
*//* geek
*//* technology aficionado
*//* biker
*//* golfer
*//* musician
*//* food lover
*//* design enthusiast
*//* [and more...](http://ustohal.eu)

{% if site.posts.size > 0 %}
Sometimes I also write:

<ul>
{% for post in site.posts %}
<li><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
{% endif %}

