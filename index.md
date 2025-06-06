---
layout: default
title: "Welcome to the Information Superhighway!"
header_title: "Welcome to My Totally Rad Blog!"
header_subtitle: "*** NEW POSTS UPDATED WEEKLY! ***"
---

## Latest Blog Entries

{% for post in site.posts limit:5 %}
<div class="post">
    <div class="post-title"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></div>
    <div class="post-date">Posted: {{ post.date | date: "%B %d, %Y" }}</div>
    {{ post.excerpt }}
    {% if post.mood %}<p><b>Current mood:</b> {{ post.mood }}</p>{% endif %}
</div>
{% endfor %}

{% if site.posts.size == 0 %}
<div class="post">
    <div class="post-title">Welcome to My Blog!</div>
    <div class="post-date">Posted: {{ site.time | date: "%B %d, %Y" }}</div>
    <p>Welcome to my totally awesome homepage! I just learned HTML and I'm super excited to share my thoughts with the entire Internet. This is like having my own TV channel but better!</p>
    <p>I spent all weekend learning how to make this page. My friend Dave showed me how to use Netscape Composer and it's pretty rad. Can't wait to add more cool stuff like animated GIFs and maybe even a Java applet!</p>
    <p><b>Current mood:</b> 😎 Excited about the Information Superhighway!</p>
</div>
{% endif %}