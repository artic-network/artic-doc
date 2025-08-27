---
title: Resources
keywords: resources
sidebar: artic_sidebar
toc: false
permalink: /resources
folder:
tags: [resources]
---

{% assign docs = site.html_pages | where_exp:"item", "item.folder == 'viruses'" %}
{% if docs and docs.size != 0 %}
<div class="row">
    <div class="col-lg-12">
        <h2 class="page-header">Viruses</h2>
    </div>
    {% for page in docs %}
        {% include subsection.html icon=page.icon title=page.title_text url=page.url summary=page.subtitle_text %}
    {% endfor %}
</div>
{% endif %}

{% assign docs = site.html_pages | where_exp:"item", "item.folder == 'protocols'" %}
{% if docs and docs.size != 0 %}
<div class="row">
    <div class="col-lg-12">
        <h2 class="page-header">Protocols</h2>
    </div>
    {% for page in docs %}
    {% include subsection.html icon=page.icon title=page.title_text url=page.url summary=page.subtitle_text %}
    {% endfor %}
</div>
{% endif %}

{% assign docs = site.html_pages | where_exp:"item", "item.folder == 'pipelines'" %}
{% if docs and docs.size != 0 %}
<div class="row">
    <div class="col-lg-12">
        <h2 class="page-header">Analysis Pipelines</h2>
    </div>
    {% for page in docs %}
    {% include subsection.html icon=page.icon title=page.title_text url=page.url summary=page.subtitle_text %}
    {% endfor %}
</div>
{% endif %}

{% assign docs = site.html_pages | where_exp:"item", "item.folder == 'software'" %}
{% if docs and docs.size != 0 %}
<div class="row">
    <div class="col-lg-12">
        <h2 class="page-header">Software</h2>
    </div>
    {% for page in docs %}
    {% include subsection.html icon=page.icon title=page.title_text url=page.url summary=page.subtitle_text %}
    {% endfor %}
</div>
{% endif %}


<!-- {% include links.html %} -->
