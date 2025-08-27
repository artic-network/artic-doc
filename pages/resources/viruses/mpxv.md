---
title: MPXV (mpox virus)
title_text: MPXV<br>(mpox virus)
subtitle_text: A collection of resources and documents for the genome sequencing of Mpox virus (MPXV)
summary: "A collection of resources and documents for the genome sequencing of Mpox virus (MPXV) using a tiled amplicon approach."
image: /images/viruses/mpxv.png
permalink: /viruses/mpxv
icon: /images/viruses/mpxv_icon.svg
folder: viruses
virus: mpxv
keywords: resources
tags: [resources, viruses]
---

## Resources and documents

{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'guide'" | sort: 'order' %}
{% if docs and docs.size != 0 %}
### Background
<ul>
{% for doc in docs %}
    <li>{{ doc.title_text }}</li>
	<blockquote>
        {{ doc.subtitle_text }} <br />
        link: <a href="{{ doc.permalink }}">{{ doc.permalink }}</a>
    </blockquote>
{% endfor %}
</ul>
{% endif %}

{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'setup'" | sort: 'title' %}
{% if docs and docs.size != 0 %}
### Setup guides
<ul>
{% for doc in docs %}
    <li>{{ doc.title_text }}</li>
	<blockquote>link: <a href="{{ doc.permalink }}">{{ doc.permalink }}</a></blockquote>
{% endfor %}
</ul>
{% endif %}

{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'epi2me'"| sort: 'title' %}
{% if docs and docs.size != 0 %}
### User-interface pipelines using Epi2me
<ul>
{% for doc in docs %}
    <li>{{ doc.title_text }}</li>
	<blockquote>link: <a href="{{ doc.permalink }}">{{ doc.permalink }}</a></blockquote>
{% endfor %}
</ul>
{% endif %}

{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'cli'" | sort: 'title' %}
{% if docs and docs.size != 0 %}
### Command line interface pipeline SOPs
<ul>
{% for doc in docs %}
    <li>{{ doc.title_text }}</li>
	<blockquote>link: <a href="{{ doc.permalink }}">{{ doc.permalink }}</a></blockquote>
{% endfor %}
</ul>
{% endif %}

{% include links.html %}
