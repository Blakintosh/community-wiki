---
layout: page
title: Mod Tools Launcher
permalink: /docs/launcher/
show_title: false
---

<section class="hero">
  <div class="hero__inner">
    <span class="hero__eyebrow">Launcher</span>
    <h1 class="hero__title">Mod Tools Launcher</h1>
    <p class="hero__lead">Applications hosted by the Black Ops III Mod Tools Launcher.</p>
  </div>
</section>

<div class="card-grid">
  {% for post in site.docs %}{% if post.section == "launcher" %}
    <a class="card" href="{{ post.url | prepend: site.baseurl }}">
      <span class="card__eyebrow">Launcher</span>
      <h3 class="card__title">{{ post.title }}</h3>
      {% if post.description %}<p class="card__desc">{{ post.description }}</p>{% endif %}
    </a>
  {% endif %}{% endfor %}
</div>
