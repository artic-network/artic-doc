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

## Background
{% assign docs = site.html_pages | where_exp:"item", "item.folder contains 'lhf'" | where_exp:"item", "item.category contains 'background'" | sort: 'order' %}
<dl>
    {% for doc in docs %}
    <dt><a href="{{ doc.permalink }}">{{ doc.title_text }}</a></dt>
    <dd>{{ doc.summary }}</dd>
    {% endfor %}
</dl>

## Resources, Protocols and Tutorials
{% assign docs = site.html_pages | where_exp:"item", "item.folder contains 'lhf'" | where_exp:"item", "item.category contains 'tutorial'" | sort: 'order' %}
<dl>
    {% for doc in docs %}
    <dt><a href="{{ doc.permalink }}">{{ doc.title_text }}</a></dt>
    <dd>{{ doc.summary }}</dd>
    {% endfor %}
</dl>



