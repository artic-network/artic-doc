---
title: Virus sequencing
keywords: resources_sidebar
summary: "Resources, primers, protocols and pipelines for sequencing viruses"
sidebar: artic_sidebar
toc: false
permalink: viruses
folder: resources
---

## Virus sequencing

About virus sequencing.

## More sample content

Current viruses.

<div class="row">
    <div class="col-lg-12">
        <h2 class="page-header">Viruses</h2>
    </div>
    {% for page in site.html_pages %}
    {% if page.folder == "viruses" %}
    <div class="col-md-4">
        <div class="media">
            <div class="pull-left">
                    <span class="fa-stack fa-2x">
                        <a class="post-link" href="{{ page.url | remove: "/" }}">
                        <img src="{{ page.image }}" alt="{{ page.title }}" class="img-responsive" style="object-fit: cover; width: 64px; height: 64px; border-radius: 25%"/></a>
                    </span>
            </div>
            <div class="media-body note-text">
                <div class="media-heading"><a class="post-link" href="{{ page.url }}">{{ page.title }}</a></div>
                <p>{% if page.summary %} {{ page.summary | strip_html | strip_newlines | truncate: 160 }} {% else %} {{ page.content | truncatewords: 50 | strip_html }} {% endif %}</p>
            </div>
        </div>
    </div>
    {% endif %}
    {% endfor %}
</div>



{% include links.html %}
