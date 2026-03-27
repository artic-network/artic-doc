---
title: Documentation, tutorials and teaching materials
keywords: training
sidebar: artic_sidebar
toc: false
permalink: /training/workshops
folder: training
---

## Workshops

{% assign docs = site.html_pages | where_exp:"item", "item.category contains 'workshop'" | sort: 'title' %}
<ul>
    {% for doc in docs %}
    <li><a href="{{ doc.permalink }}">{{ doc.title_text }}</a></li>
    {% endfor %}
</ul>



