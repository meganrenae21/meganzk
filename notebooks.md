---
title: notebooks
permalink: notebooks
isnote: false
layout: default
category: meta
---


{%- assign notebooks = site.data.notebooks -%}
<ul>
{%- for book in notebooks -%}
<li><a href="{{ book.loc }}">{{ book.subject }}</a></li>
{%- endfor -%}
</ul>