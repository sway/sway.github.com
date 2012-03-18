---
layout: post
title: "From WordPress to a book"
category: 
tags: [wordpress, latex, python]
published: false
---
{% include JB/setup %}

In the [previous post](/blog/2012/02/05/the-one-about-the-book) I have already covered the background of my book. In this post I would like to focus on the more technical part, i.e. the process of transforming the WordPress posts to a physical paper book.

## Weapons of choice
The most important decision to be made was the choice of the typesetting application/platform. On one hand there was InDesign or Quark, however, I did not have access to them in Korea. On the other hand, there was LaTeX, which is awesome, but sometimes also a drama queen. And there was the third choice, something completely different, such as Scribus.

As you can guess, I decided to go with LaTeX. I always liked complicated girls.

Next, I had to choose a language to use to parse the WordPress posts etc.. I decided to go with Python, because it can be used as a nice and powerful scripting language, especially for XML parsing.

Apart from these two, I used bash for some smaller tasks (more like automation) and Illustrator for the design of the cover.

The weaponry is ready, let's dive into the process.

## Operation: WordPress
I am sure there is a service that would to that for me --- download all the post and images, make a layout and typeset them as a book. But that would be boring and I would have to stick to some pre-defined templates. No, thank you, I am too good for that. So, how to get the posts from WordPress to LaTeX? Piece. Of. Cake.

{% highlight py linenos %}
import sys
import datetime
from pytz import timezone
from lxml import etree

kst = timezone("Asia/Seoul")
gmt = timezone("GMT")

def processPost(post):
	title = post.findtext("title").encode('utf8')
	dateStr = post.findtext("pubDate")
	dateStr = dateStr[:-6]
	
	dt_gmt = datetime.datetime.strptime(dateStr, "%a, %d %b %Y %H:%M:%S")
	dt_gmt = dt_gmt.replace(tzinfo=gmt)

	dt = dt_gmt.astimezone(kst)
	
	filename = dt.strftime("%Y-%m-%d-%H-%M-%S") + '.tex'
	
	content = post.findtext("content_encoded").encode('utf8')
	
	f = open(filename, "w")
	f.write('\\begin{post}\n')
	f.write('\t\\postdata{' + title + '}{' + str(dt.year) + '}{' + str(dt.month) + '}{' + str(dt.day) + '}{' + str(dt.hour) + '}{' + str(dt.minute) + '}{' + str(dt.second) + '}\n')
	f.write('\t\\begin{content}\n')
	f.write(content + '\n')
	f.write('\t\\end{content}\n')
	f.write('\\end{post}\n')
	f.close()		
	
file = sys.argv[1]	
blog = etree.parse(file)	
for post in blog.getiterator("item"):
	processPost(post)
{% endhighlight %}

Yes, it's ugly as hell...but it worked. It was a single purpose script, that did not need any error handling or anything. Not really programmer-like? Maybe. Fast and useful? Definitely.

This script took the WordPress XML export, scooped out all the posts and placed each post into a separate file. The "template" for the file was like this:

{% highlight latex %}
\begin{post}
	\postdata{<title>}{<year>}{<month>}{<day>}{<hour>}{<minute>}{<second>}
	\begin{content}
	<post content>
	\end{content}
\end{post}
{% endhighlight %}

By using `\postdata` custom command I retained all the important information about the post without necessarily specifying in what order I will print them out. It also allowed me to use them more than once, but I will get to that later.

## Templating
Designing the "template" comprised several steps such as chapter title, post title, headers and footers etc. Some of them were quite simple, such as using `fancyhdr` for header/footer, other however required more tinkering.



### Chapter titles
By default, every chapter begins on a new page, however, I wanted to have a standalone page just for the title. The easiest way was to use `titlesec` and `tikz` to position the title and a "subtitle" (stored in `\monthstuff`) on the page.

{% highlight latex %}
\newcommand*\chapterlabel{}
\titleformat{\chapter}
	{\gdef\chapterlabel{}\Huge\bfseries}
	{\gdef\chapterlabel{}}
	{0pt}
	{\begin{tikzpicture}[remember picture,overlay]
		\node[anchor=west,text width=\textwidth,align=left,xshift=0pt] at (0,0) {\normalfont\itshape\Large \monthstuff};
		\node[anchor=west,text width=\textwidth,align=right,xshift=-7.5pt,yshift=-150pt] at (0,0) {\TB\chapterlabel#1};
		\draw[line width=1pt,draw=Plum,yshift=-165pt](0,0) -- (\textwidth,0);
	\end{tikzpicture}}
\titlespacing*{\chapter}{0pt}{0pt}{180pt}
{% endhighlight %}


To make things even easier I defined a command `\newmonth` with two arguments --- month name and subtitle. The command then handled the assignment of the `\monthstuff` variable, typesetting of the two chunks of text and printout of the chapter TOC.

{% highlight latex %}
\newcommand{\newmonth}[2]{
	\def\monthstuff{#2}
	\chapter{#1}
	\def\monthstuff{}
	\startcontents[sections]
	\printcontents[sections]{l}{1}{\setcounter{tocdepth}{1}}
	\vfill}
{% endhighlight %}

---

The TOC for each chapter was generated using `titletoc` and the format is defined like this:

{% highlight latex %}
{% assign code2 = '\titlecontents{chapter}[1em]{}{\textbf}{\textbf}{{\L\titlerule*[5pt]{.}}\contentspage}[\vspace{2pt}]' %}
{{ code2 }}
{% endhighlight %}

### Post meta and titles
As I have already mentioned above, each post is enclosed in a `post`
environment and defines a `\postdata` command for the metadata.

{% highlight latex %}
\newcommand{\postdata}[7]{
	\def\postd{#4.#3.#2}
	\def\postmeta{Published on\ \postd\ at\ #5:#6:#7}
	\section{#1}
}
{% endhighlight %}

As you can see, this simple command defines `\postd`, which is a formatted version of the date and `\postmeta`, which is a more detailed info about date and time printed out at the end of a post. The elegance of this solution lies in the ease of customization. By changing the definition of `\postd` I can change the title of all the posts at once.

The `post` environment 

### Chapter TOC
