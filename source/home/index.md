---
title: home
date: 2017-02-16 17:13:50
type: "home"
comments: false
---
<h2>{{ page.title }}</h2>
<p>最新文章</p>
<ul>
　　{% for post in site.posts %}
　　　　<li>{{ post.date | date_to_string }} <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
　　{% endfor %}
</ul>
