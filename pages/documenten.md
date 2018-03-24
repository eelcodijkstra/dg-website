---
layout: page
title: "Documenten"
---

{%- assign my_docs = site.docs | group_by: "category" -%}
{% for cat in my_docs %}
  {%- assign cat_title = site.data.categories[cat.name].title -%}
  {%- assign cat_page = site.pages | where:"title", cat_title | first -%}
<h4><a class="page-link" href="{{ cat_page.url | relative_url }}"> {{ cat_page.title | escape }} </a></h4>

  {% for item in cat.items -%}
* <a class="page-link" href="{{ item.url | relative_url }}"> {{ item.title | escape }} </a>
  {% endfor -%}
{% endfor %}
