---
layout: default
title: "Tags"
header_title: "🏷️ Blog Tags"
header_subtitle: "Find posts by topic!"
---

<div class="link-category">
    <h3>All Tags</h3>
    {% assign all_tags = site.posts | map: 'tags' | join: ',' | split: ',' | uniq | sort %}
    {% for tag in all_tags %}
        {% assign tag_posts = site.posts | where_exp: "post", "post.tags contains tag" %}
        <div class="cool-link">
            <a href="{{ '/tag/' | append: tag | relative_url }}">{{ tag }}</a> ({{ tag_posts.size }} post{% if tag_posts.size != 1 %}s{% endif %})
        </div>
    {% endfor %}
</div>