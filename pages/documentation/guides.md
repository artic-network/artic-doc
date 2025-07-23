---
title: Documentation, tutorials and teaching materials
keywords: documentation
sidebar: artic_sidebar
toc: false
permalink: /documentation/guides
folder: documentation
---

## Guides

{% assign docs = site.html_pages | where_exp:"item", "item.category contains 'guide'" | sort: 'title' %}
<ul>
    {% for doc in docs %}
    <li><a href="{{ doc.permalink }}">{{ doc.title_text }}</a></li>
    {% endfor %}
</ul>



