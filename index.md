---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
permalink: /
title: home
category: meta
---
{%- assign notes = site.pages | where: "isnote", "true" -%}
{%- assign sorted_notes = notes | sort: "note_id" | reverse -%}

## what is this?

*megan-zk* is my personal knowledge database, loosely based on the [Zettelkasten Method](https://zettelkasten.de/)↗. Other inspiration comes from [Andy Matuschak's Evergreen Notes](https://notes.andymatuschak.org/About_these_notes)↗ as well as [this list of digital gardens](https://github.com/MaggieAppleton/digital-gardeners)↗ on Github and [this list of public zettelkastens](https://github.com/KasperZutterman/Second-Brain)↗, also on Github.

## technical info

Notes are indexed by [tag](tags) and [type](categories). Tags indicate what the note is about, while the note type indicates the structure of the note itself. Notes have a specific [structure](note-structure) and can be linked to each other via hierarchal or non-hierarchal relationships.

## recent

<ul>
{%- for note in sorted_notes limit: 10 -%}
<li><a href="{{ note.url | relative_url }}">{{ note.title }}</a> <span class="category_tag">{{ note.category }}</span></li>
{%- endfor -%}
</ul>

## favorites

<ul>
{%- for fav in sorted_notes -%}
{%- if fav.tags contains "favorite" -%}
<li><a href="{{ fav.url | relative_url }}">{{ fav.title }}</a> <span class="category_tag">{{ fav.category }}</span></li>
{%- endif -%}
{%- endfor -%}
</ul>
