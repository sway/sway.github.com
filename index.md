---
title: Honza Ustohal
layout: default
---

<section id="intro">
	<article>
		<div id="portrait">&nbsp;</div>
		<h1>
		hi! I am <strong>honza</strong>
		</h1>
	</article>
	<footer>
		<a class="next" href="#about">▽</a>
	</footer>
</section>

<section id="about">
	<article>
		<h1>who am I?</h1>
			<ul>
				<li>product manager at <a href="http://fyber.com/">Fyber</a></li>
				<li>lovable geek</li>
				<li>technology aficionado</li>
				<li>musician</li>
				<li>biker and cyclist</li>
				<li>food lover</li>
				<li>whiskey drinker</li>
				<li>design and art enthusiast</li>
			</ul>
	</article>
	<footer>
	<a class="next" href="#contact">▽</a>
	</footer>
</section>

<section id="me" class="placeholder">
	<article>
		<h1>We're definitely going to hell but we'll have all the best stories to tell. <span>//&nbsp;Frank Turner</span></h1>
	</article>
</section>

<section id="contact">
<article>
	<h1>where to find me?</h1>
		<ul>
			<li>In <strong>Berlin</strong> &#10084;</li>
			<li>twitter: <strong><a href="https://twitter.com/swaycz">@swaycz</a></strong></li>
			<li>facebook: <strong><a href="https://facebook.com/honza.ustohal">honza.ustohal</a></strong></li>
			<li>instagram: <strong><a href="https://instagram.com/itshonza">itshonza</a></strong></li>
			<li>medium: <strong><a href="https://medium.com/@swaycz">swaycz</a></strong></li>
			<li>last.fm: <strong><a href="https://last.fm/user/swaycz">swaycz</a></strong></li>
			<li>github: <strong><a href="https://github.com/sway">sway</a></strong></li>
		</ul>
</article>
</section>

<section id="berlin" class="placeholder">
	<article>
		<h1>Guten Morgen, Berlin, Du kannst so h&auml;sslich sein, so dreckig und grau <span>//&nbsp;Peter Fox</span></h1>
	</article>
</section>

{%comment%}

{% if site.posts.size > 0 %}
<article id="blog">
	<h1>I write stuff:</h1>
	<ul>
{% for post in site.posts %}
	<li>{{ post.date | date: '%m/%Y' }} // <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
	</ul>
</article>
{% endif %}

{%endcomment%}
