---
title: Bioinformatic Analysis of amplicon sequencing data with amplicon-nf
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

{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'guide'" | sort: 'order' %}
{% if docs and docs.size != 0 %}

{% include links.html %}
