---
title: Analysis Pipelines
keywords: resources
summary: "Pipelines for analysing viral sequencing data"
sidebar: artic_sidebar
toc: false
permalink: /pipelines
folder: resources
---

{% assign docs = site.html_pages | where_exp:"item", "item.folder == 'pipelines'" | sort: 'title' %}
{% if docs and docs.size != 0 %}
<div class="row">
    <div class="col-lg-12">
        <h2 class="page-header">Analysis Pipelines</h2>
    </div>
    {% for page in docs %}
    {% include subsection.html icon=page.icon title=page.title_text subtitle=page.subtitle_text keywords=page.keywords url=page.url %}
    {% endfor %}
</div>
{% endif %}


{% include links.html %}
