---
title: "LHFV Workshop Resources"
layout: page
keywords: 
tags: 
permalink: /workshops/lhf/resources.html
title_text: "ARTIC practical training: LHFV workshop."
subtitle_text: "Workshop Resources"
icon: 
document_name: "LHFV-workshop-resources"
version: v1.0.0
creation_date: 2026-03-04
last_updated: 2026-09-08
forked_from: 
author: Elli Mylona
folder: workshops
category: workshop
summary: "An ARTIC training package free to download and deliver locally"
---

The ARTIC network has developed an end-to-end training package built around scenario-realistic materials, guiding participants through the full outbreak-response workflow: from sample collection, through ARTIC amplicon-based sequencing, to ARTIC-tool-led bioinformatics analysis, phylogenetics, and epidemiological inference. The training reflects the realities of using genomics as a component of outbreak response.

The package includes foundational lectures, protocols, and tutorials for hands-on wet lab and bioinformatics work, alongside supporting documentation for planning and evaluation. Following a pilot run, the full set of materials, including the inert synthetic genomes used to simulate outbreaks, is now available for wider distribution, enabling local delivery of the training.

To get started, [download the training materials](https://s3.climb.ac.uk/quick-research-artic-training/LHFV_training_package_v1.zip) (a 2&nbsp;GB zip file) and [request the accompanying nucleic acid materials (primers, synthetic genomes)](mailto:h.j.willmott@bham.ac.uk) to set up your own local workshop. A detailed manual walks trainers through setting up, running, and evaluating the training. The ARTIC Network team is on hand to provide remote support throughout every phase of the workshop.

## What's in the package

<img width="850" src="/images/workshop-lhfv/package_contents.png" alt="LHFV training package contents">

The package is organised into four parts:

- **Planning**: manual, task lists and templates, Gantt chart
- **Wet lab**: reagents, protocols and SOPs, nucleic acid templates
- **Bioinformatics**: analysis tools, slide decks, reading list
- **Follow-up and evaluation**: feedback, quiz questions, lessons learned

## Workshop modules

The workshop is formulated to be a 5-day hands-on training, covering both wet-lab and bioinformatics methods for viral genome sequencing and analysis. It combines lab-based, and interactive classroom-based sessions on data analysis and interpretation. Participants use a simulated outbreak scenario to mimic real-world observations.

The following modules are covered:

- Introduction to genomic epidemiology
- Introduction to nanopore sequencing and ARTIC protocols
- Simulated outbreak scenario
- Consensus building and quality controls
- Introduction to phylogenetic analysis
- Showcase of ONT MinION flow cells and software (MinKNOW, EPI2ME)
- Hands-on lab sessions covering ONT library methodology, including multiplex PCR, SPRI cleanups, end-preparation, barcode ligation, adapter ligation, final library preparation, flow cell priming, and sequencing
- Sequencing monitoring and diagnosing problems
- Hands-on bioinformatics sessions running ARTIC amplicon-nf and raccoon-nf
- Phylogenetic tree interpretation

{% include file.html prefix="https://s3.climb.ac.uk/quick-research-artic-training/LHFV_training_package_v1.zip" file="" text="Download the LHFV training package (zip, ~2&nbsp;GB)" %}

{% include link-out.html url="mailto:h.j.willmott@bham.ac.uk" text="Request primers and synthetic genomes" %}

## Background

[LHFV workshop overview](/workshops/lhf/overview.html): purpose, target audience, learning objectives, and planned future development.

<details>
<summary>Resources, Protocols and Tutorials</summary>
{% assign docs = site.html_pages | where_exp:"item", "item.folder contains 'lhf'" | where_exp:"item", "item.category contains 'tutorial'" | sort: 'order' %}
<dl>
    {% for doc in docs %}
    <dt><a href="{{ doc.permalink }}">{{ doc.title_text }}</a></dt>
    <dd>{{ doc.summary }}</dd>
    {% endfor %}
</dl>
</details>
