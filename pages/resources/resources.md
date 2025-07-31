---
title: Resources
keywords: resources
sidebar: artic_sidebar
toc: false
permalink: /resources
folder:
tags: [resources]
---

<div class="row">
    <div class="col-lg-12">
        <h2 class="page-header">Viruses</h2>
    </div>
    {% for page in site.html_pages %}
    {% if page.folder == "viruses" %}
    {% include subsection.html icon=page.icon title=page.title url=page.link summary=page.summary %}
    {% endif %}
    {% endfor %}
</div>

<div class="row">
    <div class="col-lg-12">
        <h2 class="page-header">Protocols</h2>
    </div>
    {% for page in site.html_pages %}
    {% if page.folder == "protocols" %}
    {% include subsection.html icon=page.icon title=page.title url=page.link summary=page.summary %}
    {% endif %}
    {% endfor %}
</div>

<div class="row">
    <div class="col-lg-12">
        <h2 class="page-header">Software</h2>
    </div>
    {% for page in site.html_pages %}
    {% if page.folder == "software" %}
    {% include subsection.html icon=page.icon title=page.title url=page.link summary=page.summary %}
    {% endif %}
    {% endfor %}
</div>


<!-- {% include links.html %} -->
