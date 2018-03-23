---
layout: page
title: Test
---

## Test page

Dit is een testpagina, voor het uitproberen van Liquid constructies, in het
bijzonder voor het maken van lijsten van pagina's.

Pagina's met een niet-lege titel:
{%- assign select_pages = site.pages | where_exp:"item", "item.title != nil" -%}
{% for my_page in select_pages %}
* <a class="page-link" href="{{ my_page.url | relative_url }}">{{ my_page.title | escape }}</a>
{%- endfor %}

<hr>

* [Pages]({{ site.baseurl }}/pages/computational-thinking.html)
* [Computational Thinking]({{"/pages/computational-thinking.html"|relative_url}})
* dit is een opsomming (van allerlei pagina's)
* in **Markdown**

Testing some Liquid constructs:

<hr>

header pages:

{% for path in site.header_pages %}
  {%- assign my_page = site.pages | where: "path", path | first -%}
* <a class="page-link" href="{{ my_page.url | relative_url }}">{{ my_page.title | escape }}</a>
{% endfor %}



Hier voegt Liquid kennelijk soms een `<p>` toe...
de truc om deze weg te krijgen is het `-` teken bij de endfor en/of andere
Liquid-haakjes. <br>
{{ select_pages | map:"name" | inspect }}

<hr>

Pagina's met een niet-lege titel:

{% for my_page in site.pages %}
  {%- if my_page.title %}
* <a class="page-link" href="{{ my_page.url | relative_url }}">{{ my_page.title | escape }}</a>
  {%- endif -%}
{%- endfor %}

<hr>

{%- assign default_paths = site.pages | map: "path" -%}
{%- assign page_paths = site.header_pages | default: default_paths -%}
{%- assign default_titles = site.pages | map: "title" -%}

<br>titles: <br>
{{ default_titles | inspect }}
<br> paths: <br>
{{ default_paths | inspect }}
<br> and (header) page-paths: <br>
{{ page_paths  | inspect}}

Header pages:
<div class="trigger">
  {%- for path in page_paths -%}
    {%- assign my_page = site.pages | where: "path", path | first -%}
    {%- if my_page.title -%}
    <a class="page-link" href="{{ my_page.url | relative_url }}">{{ my_page.title | escape }}</a>
     - url:
    {{ my_page.url | relative_url }} <br>
    {%- endif -%}
  {% endfor -%}
</div>

<hr>
<br>

<h3>Agenda items</h3>

{%- assign my_agenda = site.agenda | sort "agendadate" -%}
{%- for item in my_agenda -%}
* <a class="page-link" href="{{ item.url | relative_url }}">
{{ item.agendadate }} - {{ item.title | escape }} </a> <br>
{% endfor -%}

<h3> ToDo's </h3>

* toevoegen van Discourse commentaar
    * werkt dit ook voor Github Pages?
* schrijven van de eerste posts.
* pagina's: inhoudsopgave, met indeling op labels/tags
* zijbalk (optioneel) voor navigatie
*
