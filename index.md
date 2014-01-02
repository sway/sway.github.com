---
title: Honza Ustohal
layout: layout-default
---

<article id="about">
	<h1>
		honza ustohal
	</h1>
		<ul>
			<li>product manager</li>
			<li>geek and technology aficionado</li>
			<li>musician</li>
			<li>biker and cyclist</li>
			<li>food lover</li>
			<li>design and art enthusiast</li>				
		</ul>				
	<footer>
		<a class="next" href="#contact">V</a>
	</footer>	
</article>

<article id="me" class="placeholder">
	<h1>Please allow me to introduce myself, I'm a man of wealth and taste <span>//&nbsp;Rolling Stones</span></h1>
</article>	

<article id="contact">
	<h1>Where to find me?</h1>
		<ul>
			<li>In <strong>Berlin</strong></li>
			<li>twitter: <strong><a href="https://twitter.com/swaycz">@swaycz</a></strong></li>
			<li>facebook: <strong><a href="https://facebook.com/honza.ustohal">honza.ustohal</a></strong></li>
			<li>instagram: <strong><a href="https://instagram.com/honzacz">honzacz</a></strong></li>
			<li>last.fm: <strong><a href="https://last.fm/user/swaycz">swaycz</a></strong></li>
			<li>github: <strong><a href="https://github.com/sway">sway</a></strong></li>
			<li>I sometimes also write <strong><a href="/#blog">here</a></strong></li>
		</ul>	
				
		<footer>
			<a class="next" href="#blog">V</a>
		</footer>		
</article>

<article id="berlin" class="placeholder">
	<h1>Guten Morgen, Berlin, Du kannst so h&auml;sslich sein, so dreckig und grau <span>//&nbsp;Peter Fox</span></h1>		
</article>	

{% if site.posts.size > 0 %}
<article id="blog">
	<h1>I write stuff:</h1>
	<ul>
{% for post in site.posts %}
	<li><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
	</ul>
</article>
{% endif %}