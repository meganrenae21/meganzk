---
title: tags
layout: default
permalink: tags
---

{%- assign all_tags = site.pages | where: "dir", "/tags/" -%}
<ul>
{%- for tag in all_tags -%}
<li><a href="{{ tag.url | relative_url }}">{{ tag.title }}</a></li>
{%- endfor -%}
