---
layout: home
title: Browse by book
nav: true
order: 1
---

<div id="tag-filters">
  <strong>Filter by tag:</strong>
  {% assign all_tags = site.pages | map: 'tags' | join: ',' | split: ',' | uniq %}
  {% for tag in all_tags %}
    {% unless tag == "" %}
      <button class="tag-btn" data-tag="{{ tag | strip }}">{{ tag | strip }}</button>
    {% endunless %}
  {% endfor %}
  <button id="clear-filters">Show All</button>
</div>

<ul id="page-list">
  {% for page in site.pages %}
    {% if page.title %}
      <li class="page-item" data-tags="{% if page.tags %}{{ page.tags | join: ',' }}{% endif %}">
        <a href="{{ page.url }}">{{ page.title }}</a>
        {% if page.tags %}
          <small>[{{ page.tags | join: ', ' }}]</small>
        {% endif %}
      </li>
    {% endif %}
  {% endfor %}
</ul>

<script>
document.addEventListener("DOMContentLoaded", function() {
  const buttons = document.querySelectorAll(".tag-btn");
  const items = document.querySelectorAll(".page-item");
  const clearBtn = document.getElementById("clear-filters");

  buttons.forEach(button => {
    button.addEventListener("click", () => {
      const tag = button.getAttribute("data-tag");
      items.forEach(item => {
        const tags = item.getAttribute("data-tags").split(",");
        item.style.display = tags.includes(tag) ? "" : "none";
      });
    });
  });

  clearBtn.addEventListener("click", () => {
    items.forEach(item => item.style.display = "");
  });
});
</script>
