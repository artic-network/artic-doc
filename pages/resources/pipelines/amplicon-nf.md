---
title: amplicon-nf&#58; A nextflow pipeline for viral amplicon sequencing data
keywords: Amplicon | Bioinformatics | Pipeline
summary: artic-network/amplicon-nf is a bioinformatics pipeline that takes sequencing reads generated from ARTIC-style viral amplicon sequencing schemes, assembles them into consensus sequences, and runs some basic quality control on the outputs.

tags:
  - protocol
permalink: /resources/amplicon-nf
toc: false
folder: pipelines
title_text: "amplicon-nf"
subtitle_text: A nextflow pipeline for viral amplicon sequencing data
icon: /images/amplicon-nf-logo.svg
---

## Description

Full documentation for running the pipeline on the command-line [is available in the github repository](https://github.com/artic-network/amplicon-nf/tree/main/docs), however, if you prefer to utilise a GUI, we have SOPs for running the pipeline using [EPI2ME](https://epi2me.nanoporetech.com/) available below.

{% assign docs = site.html_pages | where_exp:"item", "item.folder contains 'amplicon-nf'" | sort: 'order' %}
{% if docs and docs.size != 0 %}
<div class="row">
    <div class="col-lg-12">
        <h2 class="page-header">amplicon-nf EPI2ME SOPs</h2>
    </div>
    {% for page in docs %}
    {% include subsection.html icon=page.icon title=page.title_text url=page.url summary=page.subtitle_text %}
    {% endfor %}
</div>
{% endif %}