---
title: MeV (Measles virus)
tname: MeV<br>(Measles virus)
keywords: resources
summary: A collection of resources for whole genome sequencing and analysis of Measles virus (MeV)
image: /images/viruses/mev.png
sidebar: artic_sidebar
permalink: /viruses/mev
folder: viruses
tags: [resources, viruses]
---

> A collection of resources for whole genome sequencing and analysis of Measles virus (EBOV)

## Resources and documents

{% assign docs = site.html_pages | where_exp:"item", "item.category contains 'ebov'" | sort: 'title' %}
<ul>
{% for doc in docs %}
    <li>{{ doc.title_text }}</li>
	<blockquote>link: <a href="{{ doc.permalink }}">{{ doc.permalink }}</a></blockquote>
{% endfor %}
</ul>

### Setup guides
{% assign mpxvDocs = site.html_pages | where_exp:"item", "item.category contains 'mpxv-setup'" | sort: 'title' %}
<ul>
{% for doc in mpxvDocs %}
    <li>{{ doc.title_text }}</li>
	<blockquote>link: <a href="{{ doc.permalink }}">{{ doc.permalink }}</a></blockquote>
{% endfor %}
</ul>

### User-interface pipelines using Epi2me
{% assign mpxvDocs = site.html_pages | where_exp:"item", "item.category contains 'mpxv-epi2me'" | sort: 'title' %}
<ul>
{% for doc in mpxvDocs %}
    <li>{{ doc.title_text }}</li>
	<blockquote>link: <a href="{{ doc.permalink }}">{{ doc.permalink }}</a></blockquote>
{% endfor %}
</ul>

### Command line interface pipeline SOPs
{% assign mpxvDocs = site.html_pages | where_exp:"item", "item.category contains 'mpxv-cli'" | sort: 'title' %}
<ul>
{% for doc in mpxvDocs %}
    <li>{{ doc.title_text }}</li>
	<blockquote>link: <a href="{{ doc.permalink }}">{{ doc.permalink }}</a></blockquote>
{% endfor %}
</ul>

{% include links.html %}
