
<div id="tag-filters">
  <strong>Filter by tag:</strong>
  {% assign all_tags = site.pages | map: 'tags' | uniq | join: ',' | split: ',' | uniq %}
  {% for tag in all_tags %}
    {% unless tag == "" %}
      <button class="tag-btn" data-tag="{{ tag | strip }}">{{ tag | strip }}</button>
    {% endunless %}
  {% endfor %}
  <button id="clear-filters">Show All</button>
</div>

<ul id="page-list">
  {% for page in site.pages %}
    {% if page.title and page.tags %}
      <li class="page-item" data-tags="{{ page.tags | join: ',' }}">
        <a href="{{ page.url }}">{{ page.title }}</a>
        <small>[{{ page.tags | join: ', ' }}]</small>
      </li>
    {% endif %}
  {% endfor %}
</ul>

---
layout: home
title: Browse by book
nav: true
order: 1
---
