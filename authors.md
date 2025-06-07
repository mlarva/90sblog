---
layout: default
title: "Authors"
header_title: "👥 Meet the Authors"
header_subtitle: "The creative minds behind our content!"
---

<div class="link-category">
    <h3>Our Writing Team</h3>
    {% for author_entry in site.authors %}
        {% assign author_id = author_entry[0] %}
        {% assign author_data = author_entry[1] %}
        {% assign author_posts = site.posts | where: "author", author_id %}
        <div style="margin-bottom: 20px; padding: 15px; background-color: #f0f0f0; border: 2px inset #c0c0c0;">
            <div class="cool-link" style="font-size: 16px; margin-bottom: 10px;">
                <a href="{{ '/author/' | append: author_id | relative_url }}">{{ author_data.avatar }} {{ author_data.name }}</a> 
                ({{ author_posts.size }} post{% if author_posts.size != 1 %}s{% endif %})
            </div>
            <div style="font-style: italic; color: #000080;">{{ author_data.bio }}</div>
        </div>
    {% endfor %}
</div>