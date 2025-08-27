---
title: Analysis Pipelines
keywords: resources
summary: "Pipelines for analysing viral sequencing data"
sidebar: artic_sidebar
toc: false
permalink: pipelines
folder: resources
---

<div class="row">
    <div class="col-lg-12">
        <h2 class="page-header">Analysis Pipelines</h2>
    </div>
    {% for page in site.html_pages %}
    {% if page.folder == "pipelines" %}
    {% include subsection.html icon=page.icon title=page.title_text subtitle=page.subtitle_text url=page.url %}
    {% endif %}
    {% endfor %}
</div>


{% include links.html %}
