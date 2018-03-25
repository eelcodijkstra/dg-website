---
layout: page
title: "Computational thinking"
category: computational-thinking
---

(over computational thinking)

<h3> Documenten </h3>
{%- assign my_docs = site.docs | where:"category", page.category -%}
{% for item in my_docs -%}
* <a class="page-link" href="{{ item.url | relative_url }}"> {{ item.title | escape }} </a>
{% endfor -%}
