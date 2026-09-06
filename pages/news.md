---
layout: page
title: News
permalink: /news/
description: Site and community announcements.
---

Subscribe with [RSS]({{ site.baseurl }}/feed.xml) to keep up with the latest news.
For site changes, see the [commit history](https://github.com/{{ site.github_user }}/{{ site.github_repo }}/commits/{{ site.github_branch | default: 'main' }}) kept with the code base.

{% for post in site.posts limit:10 %}
<article class="post-preview">
  <span class="post-date">{{ post.date | date: "%B %d, %Y" }}</span>
  <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h2>
  {% if post.badges %}<div class="page-tags">{% for badge in post.badges %}<span class="badge badge-{{ badge.type }}">{{ badge.tag }}</span>{% endfor %}</div>{% endif %}
  {{ post.content | split:'<!--more-->' | first }}
  {% if post.content contains '<!--more-->' %}
    <a class="link-more" href="{{ site.baseurl }}{{ post.url }}">Read more &rarr;</a>
  {% endif %}
</article>
{% endfor %}

{% if site.posts.size == 0 %}
<div class="alert alert-info" role="note"><div><h4 class="alert-heading">Nothing yet</h4><div>No news posts have been published. Follow the <a href="https://discord.gg/tzzn6zAVBz" target="_blank" rel="noopener">Discord</a> for announcements in the meantime.</div></div></div>
{% else %}
Want to see more? See the <a href="{{ site.baseurl }}/archive/">News Archive</a>.
{% endif %}
