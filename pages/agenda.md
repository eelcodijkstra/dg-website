---
layout: page
title: "Agenda"
---

{%- assign my_agenda = site.agenda | sort: "agendadate" -%}
{%- for item in my_agenda -%}
* <a class="page-link" href="{{ item.url | relative_url }}">
{{ item.agendadate }} - {{ item.title | escape }} </a> <br>
{% endfor -%}
