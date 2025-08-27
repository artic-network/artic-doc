---
title: Squirrel
title_text: "Squirrel"
subtitle_text: "Some QUIck Reconstruction to Resolve Evolutionary Links"
image: /images/software/squirrel_logo.png
summary: "Squirrel provides best-practice MPXV phylogenetics and APOBEC3-reconstruction."
sidebar: artic_sidebar
permalink: /software/squirrel
icon: /images/software/squirrel_logo.png
folder: software
keywords: resources
tags: [resources, software]
---

## Why use squirrel? 

The MPXV genome is pretty challenging to work with and do reliable phylogenetics on. It is large (~200kb), has tracts of low complexity and repetitive regions, and has large deletions, which can lead to difficulties producing a reliable alignment. With squirrel, we provide a rapid way of producing reliable [alignments](#how-it-works---alignment) for MPXV and also enable maximum-likelihood [phylogenetics pipeline](#phylogenetics-options-within-squirrel) tree estimation.

The reliability of tree estimation is determined by the quality of the input genome sequences. In [QC mode](#alignment-quality-control), squirrel can flag potential issues in the MPXV sequences that have been provided for alignment (e.g. SNPs near tracts of N, clusters of unique SNPs, reversions to reference alleles and convergent mutations) and outputs these in a mask file for investigation. We suggest you use this information to examine the alignment and pay close attention to the regions flagged. Squirrel can then accept this file with suggested masks and apply it to the sequences before doing phylogenetics. 

Enrichment of APOBEC3-mutations in the MPXV population are a signature of sustained human-to-human transmission. Identifying APOBEC3-like mutations in MPXV genomes from samples in a new outbreak can be a piece of evidence to support sustained human transmission of mpox. Squirrel can run an [APOBEC3-reconstruction](#phylogenetics-options-within-squirrel) and map these mutations onto the phylogeny.

Squirrel produces a HTML report summarising some of the key outputs.

## How to cite

If you use squirrel in your work, please cite the software using the following preprint:

[Áine O’Toole, Eddy Kinganda-Lusamaki, Rachel Colquhoun, Connor Chato, Emily Scher, Chris Kent, Sam Wilkinson, Josh Quick, Nick Loman, Ana T. Duggan, Placide Mbala-Kingebeni, Andrew Rambaut. Human outbreak detection and best practice MPXV analysis and interpretation with squirrel. bioRxiv 2025.08.13.669859; doi: https://doi.org/10.1101/2025.08.13.669859](https://www.biorxiv.org/content/10.1101/2025.08.13.669859v1)

## Documentation

Full documentation on install and usage is available on the Squirrel [GitHub](https://github.com/aineniamh/squirrel).