---
title: MeV (Measles virus)
layout: page
tname: MeV<br>(Measles virus)
keywords: resources
summary: A collection of resources for whole genome sequencing and analysis of Measles virus (MeV)
image: /images/viruses/mev.png
permalink: /viruses/mev
icon: /images/viruses/mev_icon.svg
folder: viruses
virus: mev
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

{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'setup'" | sort: 'order' %}
{% if docs and docs.size != 0 %}
### Setup guides
<ul>
{% for doc in docs %}
    <li>{{ doc.title_text }}</li>
	<blockquote>link: <a href="{{ doc.permalink }}">{{ doc.permalink }}</a></blockquote>
{% endfor %}
</ul>
{% endif %}

{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'epi2me'"| sort: 'order' %}
{% if docs and docs.size != 0 %}
### User-interface pipelines using Epi2me
<ul>
{% for doc in docs %}
    <li>{{ doc.title_text }}</li>
	<blockquote>link: <a href="{{ doc.permalink }}">{{ doc.permalink }}</a></blockquote>
{% endfor %}
</ul>
{% endif %}

{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'cli'" | sort: 'order' %}
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
