---
title: raccoon
title_text: "raccoon"
subtitle_text: "Rigorous Alignment Curation: Cleanup Of Outliers and Noise"
image: /images/software/raccoon-logo.svg
summary: "Raccoon is a lightweight toolkit for alignment and phylogenetic QC workflows. It identifies problematic sites and produces mask files and summaries for downstream analyses."
sidebar: artic_sidebar
permalink: /software/raccoon
icon: /images/software/raccoon-logo.svg
folder: software
keywords: resources
tags: [resources, software]
---

<style>
  img {
    max-height: 100%;
    width: auto;
    object-fit: contain;
  }
</style>

## Use cases

### Sequence QC
- Harmonise sequence headers using metadata files (CSV/TSV) with flexible templating.
- Match sequence identifiers to metadata and flag mismatches or missing fields.
- Filter sequences by length and ambiguous base content.
- Generate combined FASTA files with structured, epidemiologically-informative headers.

### Alignment QC
- Flag clustered SNPs that may indicate contamination, recombination, or misalignment.
- Detect SNPs adjacent to low-coverage regions (Ns) or gaps, which may reflect data quality issues.
- Identify frame-breaking indels in coding regions using a GenBank reference.
- Generate detailed reports on alignment quality with visual summaries of site conservation and N-content.

### Masking
- Generate mask files to exclude suspect sites or sequences prior to phylogenetic analysis.
- Apply masks to alignments using customizable masking characters.

### Phylogenetic QC
- Assess tree topology for anomalies including long branches and unexpected clustering.
- Evaluate molecular clock assumptions via root-to-tip regression analysis.
- Detect sources of bias including APOBEC3-mediated and ADAR-induced mutations.
- Flag convergent mutations and reversion events (when ancestral state reconstruction is available).
- Identify sequences for removal prior to downstream temporal or evolutionary analyses.

## Integrated workflows

### raccoon-nf: End-to-end Nextflow pipeline

For complete phylogenetic quality-control workflows, **[raccoon-nf](https://github.com/Desperate-Dan/raccoon-nf)** integrates raccoon's modular tools with alignment and tree-building software (MAFFT, IQ-TREE) in a production-ready Nextflow pipeline. The raccoon-nf pipeline coordinates all QC steps in sequence:

1. **Sequence QC** – harmonise headers and filter sequences
2. **Alignment** – run MAFFT on combined sequences
3. **Alignment QC** – assess alignment quality and flag problematic sites
4. **Tree estimation** – build phylogenetic tree with IQTREE
5. **Tree QC** – evaluate tree topology and identify outliers

raccoon-nf can be run through the **EPI2ME** desktop interface for users without command-line expertise.


## Documentation

Full documentation on install and usage is available on the raccoon [GitHub](https://github.com/artic-network/raccoon).


## Tutorial

A comprehensive tutorial covering sequence metadata harmonisation, multiple sequence alignment, alignment curation, phylogenetic inference, and tree assessment is available at [raccoon-nf](/tutorials/raccoon-nf.html). The tutorial includes:

- Step-by-step guidance on preparing sequence and metadata files.
- Instructions for running raccoon-nf through the EPI2ME interface.
- Interpretation of QC reports and identification of common data issues.
- Best practices for curating alignments and assessing phylogenetic results.
- Interactive exercises using provided example datasets.

The tutorial is suitable for both guided workshop delivery and self-paced learning.