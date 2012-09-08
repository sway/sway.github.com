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
*//* food lover
*//* design weirdo
*//* [more about me...](http://ustohal.eu)



{% if site.posts.size > 0 %}
I sometimes also write:

<ul>
{% for post in site.posts %}
<li><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
{% endif %}

