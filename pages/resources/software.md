---
title: Software resources
keywords: resources software
summary: "Software"
sidebar: artic_sidebar
toc: false
permalink: software
folder: resources
---

<div class="row">
    <div class="col-lg-12">
        <h2 class="page-header">Software</h2>
    </div>
    {% for page in site.html_pages %}
    {% if page.folder == "software" %}
    {% include subsection.html icon=page.icon title=page.title_text subtitle=page.subtitle_text url=page.url %}
    {% endif %}
    {% endfor %}
</div>

{% include links.html %}
