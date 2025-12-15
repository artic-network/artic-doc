---
title: MPXV (mpox virus)
title_text: MPXV<br>(mpox virus)
subtitle_text: A collection of resources and documents for the genome sequencing of Mpox virus (MPXV)
summary: "A collection of resources and documents for the genome sequencing of Mpox virus (MPXV) using a tiled amplicon approach."
image: /images/viruses/mpxv.png
permalink: /viruses/mpxv
icon: /images/viruses/mpxv_icon.svg
folder: viruses
category: virus
virus: mpxv
keywords: resources
tags: [resources, viruses]
toc: false
---

## Resources and documents

{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'guide'" | sort: 'order' %}
{% if docs and docs.size != 0 %}
### Background

{% for page in docs %}
<div class="row">
        {% include subsection.html icon=page.icon title=page.title_text url=page.url summary=page.subtitle_text %}
</div>
{% endfor %}
{% endif %}

### Primer Scheme

<div class="row">
        {% include subsection.html icon="/images/software/primal-scheme.png" title="artic-inrb-mpox/2500/v1.0.0 Primer Scheme" url="https://labs.primalscheme.com/detail/artic-inrb-mpox/2500/v1.0.0/" summary="The ARTIC-network primer scheme for sequencing MPXV" %}
</div>

{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'setup'" | sort: 'title' %}
### Setup guides

<!-- Hardcode the epi2me setup guide, it's more in-depth than anything we would write and they'll keep it updated -->
<div class="row">
        {% include subsection.html icon="/images/software/epi2me-icon.png" title="EPI2ME Installation" url="https://epi2me.nanoporetech.com/epi2me-docs/installation/" summary="A guide to help you install and set up EPI2ME from the EPI2ME team" %}
</div>

{% if docs and docs.size != 0 %}
{% for page in docs %}
<div class="row">
        {% include subsection.html icon=page.icon title=page.title_text url=page.url summary=page.subtitle_text %}
</div>
{% endfor %}
{% endif %}

{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'epi2me'"| sort: 'title' %}
{% if docs and docs.size != 0 %}
### User-interface pipelines using Epi2me
{% for page in docs %}
<div class="row">
        {% include subsection.html icon=page.icon title=page.title_text url=page.url summary=page.subtitle_text %}
</div>
{% endfor %}
{% endif %}

{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'cli'" | sort: 'order' %}
{% if docs and docs.size != 0 %}

### Command line interface pipeline SOPs
{% for page in docs %}
<div class="row">
        {% include subsection.html icon=page.icon title=page.title_text url=page.url summary=page.subtitle_text %}
</div>
{% endfor %}
{% endif %}

{% include links.html %}
