---
layout: page
title: Documentation
permalink: /docs/
show_title: false
show_breadcrumbs: false
flush: true
---

{% assign guide_count = 0 %}
{% for s in site.data.toc %}{% if s.url contains 'docs/' %}
  {% assign guide_count = guide_count | plus: s.links.size %}
  {% for l in s.links %}{% if l.children %}{% assign guide_count = guide_count | plus: l.children.size %}{% endif %}{% endfor %}
{% endif %}{% endfor %}

<div class="docs-index">
  <header class="page-head">
   <div class="container">
    <nav aria-label="breadcrumb">
      <ol class="breadcrumbs">
        <li><a href="{{ site.baseurl }}/">Home</a></li>
        <li class="active">Documentation</li>
      </ol>
    </nav>
    <span class="page-head__eyebrow">Knowledge base · {{ guide_count }} guides</span>
    <h1 class="page-head__title">Documentation</h1>
    <p class="page-head__lead">Browse every guide on the wiki, grouped by topic.</p>
   </div>
  </header>

  <div class="page-body">
   <div class="container">
    {% assign n = 0 %}
    {% for section in site.data.toc %}{% if section.url contains 'docs/' %}
      {% assign n = n | plus: 1 %}
      {% assign abbr = section.url | split: '/' | last %}
      {% assign total = section.links.size %}
      {% for l in section.links %}{% if l.children %}{% assign total = total | plus: l.children.size %}{% endif %}{% endfor %}
      <section class="docs-index__section" aria-labelledby="section-{{ abbr }}">
        <div class="docs-index__head">
          <div>
            <span class="eyebrow">{% if n < 10 %}0{% endif %}{{ n }} · {{ abbr | replace: '-', ' ' }}</span>
            <h2 id="section-{{ abbr }}"><a href="{{ site.baseurl }}/{{ section.url }}" style="color:inherit;text-decoration:none">{{ section.title }}</a></h2>
          </div>
          <span class="docs-index__count">{{ total }} guide{% if total != 1 %}s{% endif %}</span>
        </div>
        <div class="card-grid">
          {% for entry in section.links %}
            <a class="card tone-{{ abbr }}" href="{{ site.baseurl }}/{{ entry.url }}">
              <span class="card__eyebrow">{{ abbr | replace: '-', ' ' }}</span>
              <span class="card__title">{{ entry.title }}</span>
              {% if entry.description %}<span class="card__desc">{{ entry.description }}</span>{% endif %}
              <span class="card__footer"><span>{% if entry.children %}{{ entry.children | size }} sub-pages{% else %}Guide{% endif %}</span><span>&rarr;</span></span>
            </a>
          {% endfor %}
        </div>
      </section>
    {% endif %}{% endfor %}
   </div>
  </div>
</div>
