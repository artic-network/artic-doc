---
tname: SARS-CoV-2<br>(COVID-19)
title: SARS-CoV-2 (COVID-19)
keywords: resources
summary: A collection of resources for whole genome sequencing and analysis of SARS-CoV-2
sidebar: artic_sidebar
image: /images/viruses/cov.png
permalink: /viruses/sars-cov-2
icon: /images/viruses/sars-cov-2_icon.svg
folder: viruses
tags: [resources, viruses]
---

>A collection of resources for whole genome sequencing and analysis of SARS-CoV-2

## Resoures and documents



> 24-Mar-2020: We have posted [an update](/resources/ncov/ncov-amplicon-v3.pdf) to the amplicon set (V3)


## Introduction

There is a pressing need to understand more about the short-term genomic epidemiology and evolution of the recently described human coronavirus (hCoV-19). Initial cases were in Wuhan City, Hubei Province, China but now cases have been confirmed both more widely in China and internationally.

Viral genome data generated prospectively during outbreaks can help provide information about relatedness to other viruses, mode and tempo of evolution, geographical spread and adaptation to human hosts. This information can be used to assist in epidemiological investigations, particularly when combined with other types of data (e.g. case counts).

The ARTIC network is making available a set of materials (see below) to assist groups in sequencing the virus including a set of primers, laboratory protocols, bioinformatics tutorials and datasets. These are mainly focused around the use of the portable Oxford Nanopore MinION sequencer, although aspects of the protocol such as the primer scheme and sample amplification may be generalised to other sequencing platforms.

The protocol relies on direct amplification of the virus using tiled, multiplexed primers. This approach has been proven to have high sensitivity and work directly from clinical samples (compared to metagenomics approaches). This protocol has been widely adopted by groups worldwide, and we are in the process of posting validation data.

The rapid development of this primer scheme is possible as the complete genome sequences for a number of cases were released shortly after the identification of the virus both on GenBank ([accession MN908947](https://www.ncbi.nlm.nih.gov/nuccore/MN908947)) and on [GISAID](http://gisaid.org). The acknowledgments for the labs and people involved in generating these sequences is given below and we wish to highlight the cooperative spirit in which this data was shared. We urge anyone who uses this protocol to share the resulting genomes to benefit the international response to this epidemic.

Please visit our <a href="https://community.artic.network">ARTIC community discussion forum</a> for updates, or follow us on <a href="https://twitter.com/NetworkArtic">Twitter (@NetworkArtic)</a>.

## Resources and documents

{% assign docs = site.html_pages | where_exp:"item", "item.category contains 'sars-cov-2'" | sort: 'title' %}
<ul>
    <li>nCoV-2019 sequencing protocol (protocols.io)</li>
        <blockquote>link: <a href="https://dx.doi.org/10.17504/protocols.io.bbmuik6w">Protocols.io</a></blockquote>

    <li>nCoV-2019 PrimalSeq sequencing primers</li>
        <blockquote>link: <a href="https://github.com/artic-network/artic-ncov2019/tree/master/primer_schemes/nCoV-2019/V3">Github (version 3)</a></blockquote>

{% for doc in docs %}
<li>{{ doc.title_text }}</li>
<blockquote>link: <a href="{{ doc.permalink }}">{{ doc.permalink }}</a></blockquote>
{% endfor %}

   <li>A quick guide to tiling amplicon sequencing and bioinformatics</li>
       <blockquote>link: <a href="/training/guides/quick-guide-to-tiling-amplicon-sequencing-bioinformatics.html">/training/guides/quick-guide-to-tiling-amplicon-sequencing-bioinformatics.html</a></blockquote>
</ul>


## Further Reading

1. Rambaut A, Phylogenetic analysis of nCoV-2019 genomes <http://virological.org/t/phylodynamic-analysis-55-genomes-04-feb-2020/356>

2. WHO's code of conduct for open and timely sharing of pathogen genetic sequence data during outbreaks of infectious disease, <https://www.who.int/blueprint/what/norms-standards/GSDDraftCodeConduct_forpublicconsultation-v1.pdf?ua=1>

## Data acknowledgements

These resources were only possible because of the genome sequence ([accession MN908947](https://www.ncbi.nlm.nih.gov/nuccore/MN908947)) released by The Shanghai Public Health Clinical Center & School of Public Health, in collaboration with the Central Hospital of Wuhan, Huazhong University of Science and Technology, the Wuhan Center for Disease Control and Prevention, the National Institute for Communicable Disease Control and Prevention, Chinese Center for Disease Control, and the University of Sydney, Sydney, Australia.

We would also like to acknowledge all the labs that shared genome sequences through the GISAID plaform. Although these data were not used directly, they confirm the genome sequence and demonstrate a current lack of diversity allowing a more sensitive sequencing protocol.

{% include wellcome-trust.html %}

{% include links.html %}
