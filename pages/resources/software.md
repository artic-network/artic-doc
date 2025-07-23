---
title: Software resources
keywords: resources software
summary: "Software"
sidebar: artic_sidebar
permalink: software
folder: resources
---

## Virus sequencing

About virus sequencing.

## More sample content

Current viruses.

<div class="row">
    <div class="col-lg-12">
        <h2 class="page-header">Software</h2>
    </div>
    {% for page in site.html_pages %}
    {% if page.folder == "software" %}
    <div class="col-md-4">
        <div class="media">
            <div class="pull-left">
                    <span class="fa-stack fa-2x">
                          <i class="fa fa-circle fa-stack-2x text-primary"></i>
                          <i class="fa fa-tree fa-stack-1x fa-inverse"></i>
                    </span>
            </div>
            <div class="media-body">
                <h4 class="media-heading"><a class="post-link" href="{{ page.url }}">{{ page.title }}</a></h4>
                <p>{% if page.summary %} {{ page.summary | strip_html | strip_newlines | truncate: 160 }} {% else %} {{ page.content | truncatewords: 50 | strip_html }} {% endif %}</p>
            </div>
        </div>
    </div>
    {% endif %}
    {% endfor %}
</div>



{% include links.html %}
