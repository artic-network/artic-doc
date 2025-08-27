---
title: Sequencing protocols
keywords: resources
summary: "Protocols for pathogen sequencing"
sidebar: artic_sidebar
toc: false
permalink: protocols
folder: resources
---

<div class="row">
    <div class="col-lg-12">
        <h2 class="page-header">Protocols</h2>
    </div>
    {% for page in site.html_pages %}
    {% if page.folder == "protocols" %}
    {% include subsection.html icon=page.icon title=page.title_text subtitle=page.subtitle_text url=page.url %}
    {% endif %}
    {% endfor %}
</div>

{% include links.html %}
