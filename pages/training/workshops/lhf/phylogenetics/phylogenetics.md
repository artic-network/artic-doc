---
title: "LHFV Workshop Tutorial | Phylogenetic Analysis using Raccoon-nf"
layout: document
keywords: workshops
tags: [workshops, protocol]
summary:
permalink: /workshops/lhf/phylogenetic_analysis.html
title_text: "Phylogenetic Analysis using Raccoon-nf"
subtitle_text: 
document_name: "phylogenetic_analysis"
version: v1.0
creation_date: 2026-03-30
last_updated: 2026-03-30
author: Áine O'Toole, Kate Duggan & Daniel Maloney
folder: lhf
category: tutorial
order: 2
toc: true
summary: Instructions for using EPI2ME to run Raccoon to align workshop data and construct phylogenetic trees.
---

{% capture files_url %}/pages/training/workshops/lhf/phylogenetics/files/{% endcapture %}
{% capture root_url %}/pages/training/workshops/lhf/phylogenetics/images/{% endcapture %}

This tutorial is a walkthrough of running `raccoon-nf` on the data produced in the workshop. For a complete guide and tutorial see:

{% include link-out.html url="https://artic.network//tutorials/raccoon-nf.html" text="Multiple sequence alignment and phylogenetics pipeline using raccoon-nf" %}

## Installing and Launching Epi2Me

If EPI2ME isn't installed, follow these instructions: <br />

{% include link-out.html url="/workshops/lhf/installing_workflows.html" text="EPI2ME installation" %}

### 1. Launch EPI2ME

Once you have successfully installed, launch EPI2ME. To access EPI2ME without creating an account, click on the three dots at the bottom of the window, and click "Continue as guest":

{% include image.html file="epi2me_2.png" prefix=root_url max-width="66%" %}

### 2. Import `raccoon-nf` Workflow

When you have successfully launched EPI2ME, you should see the following screen. Click to open the "Launch" window in the panel on the left hand side: 

{% include image.html file="epi2me_4.png" prefix=root_url max-width="66%" %}

If it is already installed, click on the `raccoon-nf` workflow: 

{% include image.html file="epi2me_9.png" prefix=root_url max-width="66%" %}

and then jump to [Step 3](#3-running-the-raccoon-nf-workflow).

 If `raccoon-nf` workflow isn't installed then click on "Import workflow" in the top right of the window, and then "Import from GitHub":

{% include image.html file="epi2me_5.png" prefix=root_url max-width="66%" %}

Install amplicon-nf by pasting `https://github.com/artic-network/raccoon-nf` into the box and clicking "Download":

{% include image.html file="epi2me_6.png" prefix=root_url max-width="66%" %}

### 3. Setting up the input data for `raccoon`

To run the `raccoon-nf` workflow on your data you will need some additional files:

1. A `fasta` file containing background genomes from previous outbreaks of LHFV. 

2. A CSV file containing the metadata for the samples that have been sequenced.

For this workshop these can be downloaded from here:

{% include file.html file="lhfv_raccoon-nf.zip" text="lhfv_raccoon-nf.zip" prefix=files_url %}

Uncompressing (expanding) this ZIP file will produce a folder with the required files in it:

{% include image.html file="lhfv_raccoon-nf_folder.png" prefix=root_url max-width="66%" %}

Now copy the consensus genome fasta file from the output of `amplicon-nf` into this folder. This file will be called `lhfv_reference.artic-training-lhf_600_v1.0.0.combined_consensus.fasta`:

{% include image.html file="amplicon-nf_output_folder.png" prefix=root_url max-width="66%" %}

After copying this file the `lhfv_raccoon-nf` should look like this:

{% include image.html file="lhfv_raccoon-nf_folder_2.png" prefix=root_url max-width="66%" %}

### 4. Running the `raccoon-nf` workflow

Click on the 'raccoon-nf' workflow to open it:

{% include image.html file="raccoon-nf_1.png" prefix=root_url max-width="66%" %}

Click the 'Launch' button to start an instance of this workflow. 

Click on "Select a path" in the "Input sequences in fasta format" setting and in the file chooser that appears select the `lhfv_raccoon-nf` folder. Raccoon will pick up both the fasta files in here (your data and the background data) and combine them automatically:

{% include image.html file="raccoon-nf_2.png" prefix=root_url max-width="66%" %}

Click on "Select a path" in the "Input metadata file(s) for your fasta file." setting and in the file chooser that appears select the `case_metadata.csv` file in the `lhfv_raccoon-nf` folder. 

{% include image.html file="raccoon-nf_3.png" prefix=root_url max-width="66%" %}

The `case_metadata.csv` file looks like this, providing location and collection dates for each sample:
```
sample	country	location	location2	date
PHL001	Articia	Mylona_Marsh	Moranga_Moor	2025-12-03
PHL002	Articia	Mylona_Marsh	Moranga_Moor	2025-12-08
PHL003	Articia	Mylona_Marsh	Moranga_Moor	2025-12-28
PHL004	Articia	Mylona_Marsh	Quaye_Quay	2026-01-02
PHL005	Articia	Mylona_Marsh	Donkor_Dale	2026-01-03
PHL006	Articia	Mylona_Marsh	Elliville	2026-01-05
PHL007	Articia	Mylona_Marsh	Bedeburgh	2026-01-10
PHL008	Articia	Mylona_Marsh	Faux_Kent	2026-01-17
PHL009	Articia	Mylona_Marsh	Moranga_Moor	2026-01-20
.
.
.
```

Finally click the "Launch workflow" button and wait until the workflow completes:

{% include image.html file="raccoon-nf_4.png" prefix=root_url max-width="66%" %}

### 5. Examining `raccoon-nf` output reports and files

Once the workflow has finished, click on `Reports` to show the output report documents. The first three reports are from EPI2ME about how the workflow ran - unless there is a problem, these can be ignored.

The last three reports are the outputs of the various stages of `raccoon-nf` focusing on quality control (qc):

{% include image.html file="raccoon-nf_5.png" prefix=root_url max-width="66%" %}

- `seq-qc_report`: QC report on the input sequences to find possible sequencing or assembly issues.

- `aln-qc_report`: QC report on the multiple sequence alignment which identifies sequences with insufficient data to do phylogenetic analysis (these will have been removed automatically).

- `tree-qc_report`: The final phylogenetic tree report.

If you select the `tree-qc_report` option you will be able to view the report in the EPI2ME window:

{% include image.html file="raccoon-nf_5b.png" prefix=root_url max-width="66%" %}

Browse these file and look at the various sections. 

For more information about these reports see the full `raccoon-nf` tutorial:

{% include link-out.html url="https://artic.network//tutorials/raccoon-nf.html" text="Multiple sequence alignment and phylogenetics pipeline using raccoon-nf" %}

### 6. Opening the phylogenetic tree in PearTree

`raccoon-nf` produced a phylogenetic tree file that we can explore in more detail using a tool called `PearTree`. This is available as a webtool at: [http://peartree.live](http://peartree.live) or you can download desktop apps for most operating systems from here: [PearTree Downloads](http://github.com/artic-network/peartree/releases/latest).

Find the tree file that was generated by `raccoon-nf` by clicking on the 'Files' tab in your EPI2ME window. Click on `all_samples` then `tree`  and click the `...` on the line labelled `all_samples.aln.fasta.treefile`:

{% include image.html file="raccoon-nf_8.png" prefix=root_url max-width="66%" %}

Finally drag the file `all_samples.aln.fasta.treefile` into the `PearTree` webpage:

{% include image.html file="peartree_1.png" prefix=root_url max-width="66%" %}

The tree will now open in `PearTree` ready for investigation:

{% include image.html file="peartree_2.png" prefix=root_url max-width="66%" %}

{% include callout.html type="info" content="You can also use the \"Open...\" button to select the file directly" %}
