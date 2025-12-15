---
title: "Fieldbioinformatics: viral amplicon sequencing bioinformatics SOP"
layout: document
keywords: protocol
tags: [protocol]
permalink: /fieldbioinformatics/fieldbioinformatics-sop.html
title_text: "<strong>Fieldbioinformatics</strong>: viral amplicon sequencing bioinformatics SOP"
subtitle_text: "Nanopore | bioinformatics"
document_name: "fieldbioinformatics-SOP"
version: v1.0.0
creation_date: 2024-08-20
last_updated: 2025-08-27
author: Sam Wilkinson
citation: "Loman *et al.* In Prep."
folder: fieldbioinformatics | cli | mev | mpxv
icon: /images/software/field-bioinformatics-icon.png
category: cli
order: 2
---

{% include callout.html
type='default'
content='**Overview:** A complete bioinformatics protocol to take the output from the [sequencing protocol](/viruses/mpxv/artic-mpxv-guide.html) to consensus genome sequences. Includes mapping, polishing and consensus generation.
'
%}

## Preparation

If you are using a windows PC we recommend that you do any bioinformatics in a WSL2 environment, a tutorial for installing WSL2 is available here: [Microsoft WSL Install Tutorial](https://learn.microsoft.com/en-us/windows/wsl/install), this will be required before moving to the next steps.

Firstly, you will need Conda >= v23.10.0 (or a lower version with mamba installed), this will handle installation of software that the pipeline needs to run. You can find the appropriate installer for miniforge (a conda distribution) by going to this link: [miniforge downloads](https://conda-forge.org/download/), if you are using WSL2 you should download the Linux version of the installer.

Once you have downloaded the installer you can install it by opening a terminal session, moving to the path where the file was downloaded, then running it, like this:

```bash
bash Miniforge3-Linux-x86_64.sh
```

You will then be asked to confirm the install location of miniforge, it defaults to the current users home directory (`~/miniforge3/`) which is fine for the majority of usecases. After, you will be asked to read and agree the end-user license agreement, once you have done so enter `yes` to agree. 
Miniforge will then install into the previously specified directory, after which you will be asked if you would like to automatically initialise Conda when starting a new terminal session, most users will want to select `yes` here.

Once this completes you should have a working Conda install and can move onto the next step.


### Creating the environment

For the first time only, you will need to create a conda environment and install the pipeline:

```bash
conda create -n artic bioconda::artic
```

This has created a conda environment named ```artic``` containing all the software requirements for the fieldbioinformatics pipeline, you can activate this environment like so:

```bash
conda activate artic
```

## Make a new directory for analysis

Give your analysis directory a meaningful name, e.g.. analysis/run_name

```bash
mkdir analysis
cd analysis

mkdir run_name
cd run_name
```

## Read filtering

Because ARTIC protocol can generate chimeric reads, we perform length filtering.

This step is performed for each barcode in the run.

We first collect all the FASTQ files into a single file.

To collect and filter the reads for barcode03, we would run:

```bash
artic guppyplex --min-length 1500 --max-length 3000 --directory output_directory/barcode03 --prefix run_name
```

This will perform a quality check. If you are only using "pass" reads you can speed up the process with:

```bash
artic guppyplex --skip-quality-check --min-length 1500 --max-length 3000 --directory output_directory/barcode03 --prefix run_name
```

We use a length filter here of between 1500 and 3000 to remove obviously chimeric reads.

> **It is important to note that this SOP is using MPXV as an example so the min/max length thresholds are appropriate for that primer scheme. These numbers are appropriate for the 2500 length `artic-inrb-mpox` scheme but would not be appropriate for the 400 length `artic-measles` scheme**

You will now have a files called: ``run_name_barcode03.fastq``

## Run the MinION pipeline

Fieldbioinformatics uses the [clair3 variant caller](https://www.nature.com/articles/s43588-022-00387-x), previously both medaka and clair3 were available but problems with medaka forced our adoption of clair3 as the only workflow. This requires the selection of an appropriate model based upon the flowcell chemistry, sequencing speed, basecaller preset, and version. The pipeline will try to select an appropriate model based upon the `basecall_model_version_id` flag in the read file header (the sequencing instrument adds this by default), if this is not present or the pipeline cannot decide on an appropriate model you should provide one using the `--model` parameter.

If you install the pipeline via conda by default only r9.4.1 models will be available, the pipeline can automatically fetch the pre-trained r10.4.1 models from the [ONT Rerio repository](https://github.com/nanoporetech/rerio/tree/master/clair3_models) by running the following command:

```sh
artic_get_models
```

By default models are stored in the users conda environment `$CONDA_PREFIX/bin/models` however this may be changed to another location if desired in the `artic_get_models` and `artic minion` commands by using the `--model-dir` argument.

The following command will automatically pull primer schemes from the [PrimalScheme primerschemes repository](https://github.com/quick-lab/primerschemes) based on the ```--scheme-name```, ```--scheme-version```, and ```--scheme-length``` arguments, the scheme length arg is optional in most cases since the vast majority of primer schemes are only available in a single amplicon length. If the scheme you specify in this command is available in multiple different lengths you will be prompted to specify which length should be downloaded.
If a scheme supports automatic reference selection (currently only artic-inrb-mpox) the pipeline will attempt to determine the most appropriate reference sequence for your data (e.g. clade-ib) and download a version of the scheme remapped to that reference during the pipeline.

For each barcode you wish to process (e.g. run this command 12 times for 12 barcodes), replacing the file name and sample name as appropriate:

E.g. for barcode03
```bash
artic minion --normalise 200 --threads 4 --scheme-directory ~/primer_schemes --scheme-name artic-inrb-mpox --scheme-length 2500 --scheme-version v1.0.0 --read-file run_name_barcode03.fastq samplename
```

## Custom primer schemes

If you wish to utilise a custom primer scheme not available in the PrimalScheme repository you may instead provide the scheme bedfile and reference fasta directly using the ```--bed``` and ```--ref``` arguments, for example:

```bash
artic minion --normalise 200 --threads 4 --bed ~/primer_schemes/some-scheme/some_virus.scheme.bed --ref ~/primer_schemes/some-scheme/some_virus.reference.fasta --read-file run_name_barcode03.fastq
```

## Output files

   * ``samplename.rg.primertrimmed.bam`` - BAM file for visualisation after primer-binding site trimming
   * ```samplename.trimmed.bam``` - BAM file with the primers left on (used in variant calling)
   * ``samplename.merged.vcf`` - all detected variants in VCF format
   * ```samplename.pass.vcf``` - detected variants in VCF format passing quality filter
   * ```samplename.fail.vcf``` - detected variants in VCF format failing quality filter
   * ```samplename.primers.vcf``` - detected variants falling in primer-binding regions
   * ``samplename.consensus.fasta`` - consensus sequence
   * ``samplename.amplicon_depths.tsv`` - a TSV (tab delimited) file containing mean amplicon depths across the genome

To put all the consensus sequences in one file called ```my_consensus_genomes.fasta```, run

```bash
cat *.consensus.fasta > my_consensus_genomes.fasta
```
