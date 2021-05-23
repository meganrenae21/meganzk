---
layout: default
title: categories
permalink: categories
---

{%- assign all_categories = site.pages | where: "dir", "/categories/" -%}
<ul>
{%- for cat in all_categories -%}
<li><a href="{{ cat.url | relative_url }}"><b>{{ cat.title }}</b></a> {{ cat.description }}</li>
{% endfor -%}
</ul>
