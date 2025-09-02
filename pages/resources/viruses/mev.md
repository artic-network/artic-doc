---
title: MeV (Measles virus)
layout: page
title_text: MeV<br>(Measles virus)
subtitle_text: A collection of resources for whole genome sequencing and analysis of Measles virus (MeV)
summary: A collection of resources for whole genome sequencing and analysis of Measles virus (MeV)
image: /images/viruses/mev.png
permalink: /viruses/mev
icon: /images/viruses/mev_icon.svg
folder: viruses
category: virus
virus: mev
keywords: resources
tags: [resources, viruses]
toc: false
---
     
## Resources and documents


### Background
{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'background'" | sort: 'order' %}
{% if docs and docs.size != 0 %}

{% for page in docs %}
<div class="row">
        {% include subsection.html icon=page.icon title=page.title_text url=page.url summary=page.subtitle_text %}
</div>
{% endfor %}
{% endif %}


{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'setup'" | sort: 'order' %}
{% if docs and docs.size != 0 %}
<!-- ### Setup guides
{% for page in docs %}
<div class="row">
        {% include subsection.html icon=page.icon title=page.title_text url=page.url summary=page.subtitle_text %}
</div>
{% endfor %}
{% endif %}
-->

{% assign docs = site.html_pages | where_exp:"item", "item.folder contains page.virus" | where_exp:"item", "item.category contains 'epi2me'"| sort: 'order' %}
{% if docs and docs.size != 0 %}
### User-interface pipelines using Epi2me
<!-- Hardcode the epi2me setup guide, it's more in-depth than anything we would write and they'll keep it updated -->
<div class="row">
        {% include subsection.html icon="/images/software/epi2me-icon.png" title="EPI2ME Installation" url="https://epi2me.nanoporetech.com/epi2me-docs/installation/" summary="A guide to help you install and set up EPI2ME from the EPI2ME team" %}
</div>

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
