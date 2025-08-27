---
title: amplicon-nf&#58; A nextflow pipeline for viral amplicon sequencing data
keywords: Amplicon | Bioinformatics | Pipeline
tags:
  - protocol
permalink: /resources/amplicon-nf
folder: pipelines
title_text: "amplicon-nf"
subtitle_text: A nextflow pipeline for viral amplicon sequencing data
icon: /images/protocols/amplicon.svg
---

## Resources and documents

{% assign docs = site.html_pages | where_exp:"item", "item.folder == 'amplicon-nf'" | sort: 'title' %}
{% if docs and docs.size != 0 %}
### Setup guides
<ul>
{% for doc in docs %}
    <li>{{ doc.title_text }}</li>
	<blockquote>link: <a href="{{ doc.permalink }}">{{ doc.permalink }}</a></blockquote>
{% endfor %}
</ul>
{% endif %}