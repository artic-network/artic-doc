---
title: EBOV (Ebola virus)
title_text: EBOV<br>(Ebola virus)
subtitle_text: A collection of resources for whole genome sequencing and analysis of Ebola virus (EBOV)
summary: A collection of resources for whole genome sequencing and analysis of Ebola virus (EBOV)
image: /images/viruses/ebov_cdc.png
sidebar: artic_sidebar
permalink: /viruses/ebov
icon: /images/viruses/ebov_icon.svg
folder: viruses
category: virus
keywords: resources
tags: [resources, viruses]
---

> A collection of resources for whole genome sequencing and analysis of Ebola virus (EBOV)

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
