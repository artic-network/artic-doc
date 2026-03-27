---
title: "LHF Workshop Overview"
layout: page
keywords: 
tags: 
permalink: /workshops/lhf/resources.html
title_text: "ARTIC practical training: LHFV workshop."
subtitle_text: "Workshop Resources"
icon: 
document_name: "LHF-workshop-resources"
version: v1.0.0
creation_date: 2026-03-04
last_updated: 2026-03-04
forked_from: 
author: Elli Mylona
folder: workshops
category: workshop
summary: "overview of LHF workshop"
---

{% assign docs = site.html_pages | where_exp:"item", "item.category contains 'lhf'" | sort: 'title' %}
<ul>
    {% for doc in docs %}
    <li><a href="{{ doc.permalink }}">{{ doc.title_text }}</a></li>
    {% endfor %}
</ul>


