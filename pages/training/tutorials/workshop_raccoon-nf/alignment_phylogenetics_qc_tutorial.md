---
title: "Alignment and Phylogenetics QC Tutorial | Raccoon-nf"
layout: document
keywords: tutorial
tags: [tutorial, protocol]
summary:
permalink: /tutorials/raccoon-nf.html
title_text: "Multiple sequence alignment and phylogenetics pipeline using raccoon-nf"
subtitle_text: "Raccoon | phylogenetics"
document_name: "ARTIC-raccoon-nf-tutorial"
version: v1.0
creation_date: 2026-03-15
last_updated: 2026-03-15
author: Áine O'Toole, Kate Duggan & Daniel Maloney
citation: https://github.com/artic-network/raccoon
image: /images/software/raccoon-logo.svg
icon: /images/software/raccoon-logo.svg
folder: training
category: tutorial
order: 2
---

<style>
  img {
    max-width: 50%;
    height: auto;
    display: block;
  }
</style>

{% include callout.html
type='default'
content='
**Overview:** A complete tutorial to combine newly generated consensus genome sequences with background and metadata, running sequence and metadata quality control, multiple sequence alignment, site masking or problematic sequence removal, maximum likelihood phylogenetic inference, and tree quality assessment. The software tools used today include the raccoon toolkit, MAFFT and IQTREE, run through a Nextflow pipeline within the EPI2ME interface.  Raccon, MAFFT and IQTREE can be used as command line tools, with full command-line documentation available for raccoon available at [github.com/artic-network/raccoon](https://github.com/artic-network/raccoon).
'
%}

## Table of Contents

- [Background](#background)
- [Learning outcomes](#learning-outcomes)
- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [1. Understanding and exploring the datafiles](#1-understanding-and-exploring-the-datafiles)
- [2: Understanding raccoon-nf pipeline](#2-understanding-raccoon-nf-pipeline)
- [3. Running raccoon-nf in EPI2ME](#3-running-raccoon-nf-in-epi2me)
- [4. Interpreting the output of raccoon-nf](#4-interpreting-the-output-of-raccoon-nf)
  - [seq-qc](#4-interpreting-the-output-of-raccoon-nf-seq-qc)
  - [aln-qc](#4-interpreting-the-output-of-raccoon-nf-aln-qc)
  - [tree-qc](#4-interpreting-the-output-of-raccoon-nf-tree-qc)
- [Discussion](#discussion)
- [Additional Resources](#additional-resources)

---

{% capture files_url %}{{ site.tutorials_root_url }}/workshop_raccoon-nf/files/{% endcapture %}
{% capture root_url %}{{ site.tutorials_root_url }}/workshop_raccoon-nf/images/{% endcapture %}


## Background

Working with multiple FASTA files and creating clear, informative headers for phylogenetic analysis can be much easier with the right tools and guidance. For those who may be less familiar with coding or the command line, tasks such as merging FASTA files or structuring metadata-rich headers can be time-consuming, especially when done manually. This tutorial introduces practical approaches that simplify these steps and help reduce the chance of errors in metadata or sequence entries.

In addition, understanding and critical evaluation of the quality of results is an important part of viral phylogenetics. This tutorial will guide you through sequence quality-control steps, highlight potential issues that can arise during multiple sequence alignment, and help you confidently assess and interpret the resulting phylogenetic trees.

In this tutorial, the pipeline will be run using the EPI2ME user interface. Users do not need to run every command manually, and do not need knowledge of the command line to run raccoon, however they should understand each stage. Users that are familiar with the command line can run different modules independently in their own custom workflows to aid in post-consensus analysis QC.

---

## Learning outcomes

By the end of the session, participants should be able to:

- Explain why metadata harmonisation is essential before phylogenetic analysis.
- Identify common metadata and sequence quality problems and describe their downstream impact.
- Understand the importance of alignment curation, and the impact of alignment issues on phylogenetic inference.
- Appreciate the importance of background data and sampling bias.
- Interpret key outputs from raccoon modules `seq-qc`, `aln-qc`, and `tree-qc`.
- Critically assess root-to-tip plots, read a phylogenetic tree structure, and understand phylogenetic structure that may indicate upstream analytical issues.

---


## Prerequisites

This tutorial assumes the following software is installed:

- Docker
- EPI2ME

---

## Setup

{% include image.html file="epi2me_1.png" prefix=root_url %} <br />

{% include enum.html number='1' content='Today we will run the raccoon-nf pipeline through the [EPI2ME](https://labs.epi2me.io/downloads/) user interface. Please first install the EPI2ME desktop application using the provided link. Follow the setup instructions in the package to install and run EPI2ME.' %}

   {% include image.html file="epi2me_2.png" prefix=root_url %} <br />

{% include enum.html number='2' content='Once you have successfully installed, launch EPI2ME.' %}

   {% include image.html file="epi2me_3.png" prefix=root_url %} <br />

{% include enum.html number='3' content='To access EPI2ME without creating an account, click on the three dots at the bottom of the window, and click "Continue as guest".' %} 

   {% include image.html file="epi2me_4.png" prefix=root_url %} <br />

{% include enum.html number='4' content='When you have successfully launched EPI2ME, you should see the above screen. To install the raccoon-nf pipeline, click to open the "Launch" window in the panel on the left hand side.' %}

   {% include image.html file="epi2me_5.png" prefix=root_url %} <br />

{% include enum.html number='5' content='Click on "Import workflow" in the top right of the window, and then "Import from GitHub".' %}

   {% include image.html file="epi2me_6.png" prefix=root_url %} <br />

{% include enum.html number='6' content='To import the raccoon-nf workflow, paste "https://github.com/Desperate-Dan/raccoon-nf" into the box and click "Download".' %}

   {% include image.html file="epi2me_7.png" prefix=root_url %} <br />

{% include enum.html number='7' content='You should see the above screen if the workflow installed correctly. Click "Open" to launch the workflow.' %}


---

## 1. Understanding and exploring the datafiles

### Concepts to cover

- FASTA and metadata formats
- The content of the provided files

### Steps
{% include enum.html number='1' content='Phylogenetic analysis requires two main types of data: sequence data, in the form of a FASTA file, and metadata, in the form of a TSV (tab separated value) or CSV (comma separated value) file. Often metadata is stored in spreadsheets, such as in Microsoft Excel or Google sheets. If you download a set of sequence data from [Pathoplexus](https://pathoplexus.org/), the accompanying metadata is available as a TSV.' %}
 
{% include enum.html number='2' content='FASTA files' %}

   A FASTA-formatted file contains sequence records, which can be amino acid or nucleotide sequences. A record minimally contains two pieces of information:

   - The sequence ID (e.g. PP00001)
   - The sequence itself (e.g. CGATCGAT...ACTGACT)

   Format details:

   - The sequence ID is stored in the header line, denoted by a `>` symbol
   - The header line may also contain additional information (sequence description) after the first space
   - Important: The sequence ID must not contain whitespace (spaces or tabs)
   - The sequence is stored on the following line(s)
   - Sequences can be split across multiple lines for readability
   - The next record does not start until the next line that begins with `>`

{% include question.html content='Select which of the following are good/ valid FASTA records: <br> 
   a)`>PP00010 barcode=barcode01` <br>
   `AGCTAGCTAGCGTAGCTAGCGCATTACGTACTACG`<br>
   `AGCTAGCTAGCGTAGCTAGCGCATTACGTACTACG`<br>
   `AGCTAGCTAGCGTAGCTAGCGCATTACGTACTACG` <br>
   <br>
   b)`>PP 00011`<br>
   `AGCTAGCTAGCGTAGCTAGCGCATTACGTACTACG`<br>
   `GGCTAGCTAGCGTAGCTAGCGCATTACGTACTACT`<br>
   `TGCTAGCTAGCGTAGCTAGCGCATTACGTACTACA`<br>
   `ACGTAGTCATAGTCGTACTGAC`<br>
   <br>
   c)`PP00012`<br>
   `AGCTAGCTAGCGTAGCTAGCGCATTACGTACTACG`<br>
   <br>
   d)`>PP00013|inis_aine|2026-03-16`<br>
   `AGCTAGCTAGCGTAGCTAGCGCATTACGTACTACG`<br>
   `AGCTAGCTAGCGTAGCTAGCGCATTACGTACTACG`
   '
%}

{% include enum.html number='3' content='Metadata files' %}

In order to properly inform our analysis, we need to integrate our sequence data with sequence metadata. Metadata is data that provides additional information about our samples, such as collection date or location. This is ususally supplied as an additional file in CSV or TSV format.

Depending on the data collection process, planning, and ethics approvals, metadata may be very detailed or more sparse. 

{% include question.html content='Rank the following types of metadata in order of how useful they may be for genomic epidemiology: <br>
`Location`, `immune status`,`travel history`, `sample collection date`, `ct value`, `symptoms`, `symptom onset date`, `gender`, `age`, `occupation`, `patient eye colour`, `patient height`' %}

{% include question.html content='Which date format should be used as a standard?' %}

{% include question.html content='Why should we standardise date formats?' %} 

{% include enum.html number='4' content='In this tutorial, you will have *two* FASTA files: a set of background sequence records, and a set of *newly generated* consensus sequences that you need to fit into the known diversity and interpret. <br><br>

We are also providing metadata files to accompany the sequence data. Much of the work in preparing metadata files has already been done, however use these files as a guide for future analyses.<br><br>
<strong>Download and unzip the provided files:</strong>
[raccoon_tutorial_data.zip](https://github.com/artic-network/raccoon/blob/main/docs/tutorial/input/raccoon_tutorial_data.zip)
<br><br>
If you have carried out a sequencing run as part of the workshop and have new case data, use that file. Otherwise, a FASTA file of case data can be downloaded from [here](https://github.com/artic-network/raccoon/blob/main/docs/tutorial/input/csaes.fasta.zip).' %}

{% include enum.html number='5' content='Open the input files in a text editor.' %}

{% include question.html content='What information is provided in 1) the FASTA file and 2) the metadata files?' %}

{% include question.html content='What column contains the sequence ID?' %}

{% include question.html content='What column contains the sample date?' %}

{% include question.html content='What column contains the most detailed location data?' %}

{% include question.html content='What other information would be useful for our analysis/ interpretation?' %}


---

## 2: Understanding raccoon-nf pipeline

### Concepts to cover
- What steps are run as part of the raccoon-nf pipeline

### Pipeline details

Running best-practice phylogenetics can be challenging, however with the raccoon-nf pipeline a simple alignment and phylogenetic workflow can be performed in a single step. The pipeline itself is configurable, however in this tutorial we will be running the steps shown in the figure below.

{% include image.html file="raccoon_pipeline.svg" prefix=root_url %} <br />


A) *Input files*
- input sequences (one or more fasta files or directory containing fasta file)
- input metadata (one or more metadata files (csv or tsv) or directory containing metadata files)

B) *raccoon seq-qc*

Outputs:
- a combined fasta file with sequence headers harmonised and populated from the metadata fields
- seq-qc_report.html (a report describing the dataset, the matching, the output and any issues identified with the data)
- seq-qc_filter_failures.csv (sequences that do not pass qc filters, max n and min length)
- seq-qc_metadata_issues.csv (flagging missing metadata fields or sequences that failed to match metadata)

C) *alignment*

Multiple sequence alignment is a key step prior to running phylogenetics. It is the scaffold upon which we can begin to reconstruct the evolutionary relationships between different sequences in the tree. We will run alignment using [MAFFT](https://academic.oup.com/nar/article/30/14/3059/2904316), which is a popular software tool for creating multiple sequence alignments. 

Output:
- An aligned fasta file

D) *raccoon aln-qc*

 A high-quality alignment is crucial to generating a good phylogenetic tree. Being able to accurately assess whether there are issues with your multiple sequence alignment is a key skill that we will cover today. 
 
 The alignment is checked for various issues that may impact the quality of the phylogenetic inference. Different kinds of SNPs (clustered SNPs, N-adjacent SNPs, gap-adjacent SNPs) are flagged that may suggest issues with the alignment or with a given sequence. If a given sequence has many issues flagged (default >20), that sequence is flagged for removal from the analysis. Flagged SNPs do not necessarily mean there is anything wrong with the SNP, it may reflect genuine biological variation. However, these sites may need to be investigated closely.

Output:
- aln-qc_report.html (a report describing the input alignment, n content and any SNPs that were flagged as possibly pro)
- mask_sites.csv (describes the sites flagged for investigation or masking and the sequences flagged for removal)

E) *tree estimation*
Tree building is run using [IQTREE](https://academic.oup.com/mbe/article/37/5/1530/5721363). The substitution model used is configurable and an outgroup can optionally be included. If an outgroup is included, ancestral state reconstruction will be run during the tree building process to provide additional checks on the tree, and the outgroup sequence will be pruned off from the final tree. In this case, as we are not yet familiar with the data, we will not select an outgroup as it is not clear what an appropriate outgroup would be.

Key output:
- *.treefile (a maximum likelihood tree file)

F) *raccoon tree-qc*

Output:
- tree-qc_report.html (report showing the tree, a root to tip and any issues that were flagged during the tree-qc process)
- *.phylo_flags.csv
- A midpoint rooted tree (if no outgroup provided)
- Branch reconstruction file (if outgroup provided)
- State difference file (if outgroup provided)

---
## 3. Running raccoon-nf in EPI2ME

### Concepts to cover
- Launching a workflow in EPI2ME
- Configuring the raccoon-nf workflow settings to match the input data


   {% include image.html file="epi2me_raccoon1.png" prefix=root_url %} <br />

### Steps

{% include enum.html number='1' content='To launch an instance of the raccoon-nf workflow, click the "Launch" button.' %}

   {% include image.html file="epi2me_raccoon2.png" prefix=root_url %} <br />

{% include enum.html number='2' content='This will open the above window, with all the configuration options for the analysis. Minimally, the pipeline requires a FASTA input to run. Today we will run with two FASTA files (background historical data, and the newly sequenced case sequence data) and the two metadata files with a row corresponding to each of the sequence records.' %}

   {% include image.html file="epi2me_raccoon3.png" prefix=root_url %} <br />

{% include enum.html number='3' content='If you haven\'t already, make sure to download and unzip [raccoon_tutorial_data.zip](https://github.com/artic-network/raccoon/blob/main/docs/tutorial/input/raccoon_tutorial_data.zip). Drag your newly sequenced case FASTA file to the same directory, as shown above. The directory should now contain four files.' %}

{% include enum.html number='4' content='In the `Input Options` panel, select the directory that contains your FASTA files (it should have unzipped into a directory called "raccoon_tutorial_data"), and select the same directory for your metadata files. Raccoon-nf will automatically detect which files present are FASTA files and which ones are metadata files based on the file extensions (i.e. `.fasta` or `.csv`/`.tsv`). We can leave the remaining `Input options` as default.' %}

{% include enum.html number='5' content='We will leave pipeline options as default for this tutorial, but feel free to explore the configurable pipeline settings.' %}

   {% include image.html file="epi2me_raccoon4.png" prefix=root_url %} <br />

{% include enum.html number='6' content='Click into Sequence QC options. We can tell you we know the example genome is ~3,200 nucleotide bases in length. When setting up our raccoon-nf run, we want to include genome sequences that are complete, or nearly complete genomes.' %} 

{% include question.html content='What would a sensible minimum sequence length be for this analysis?' %}

{% include question.html content='What would a good maximum N content be? What are the tradeoffs?' %}

{% include image.html file="epi2me_raccoon5.png" prefix=root_url %} <br />

{% include enum.html number='7' content='Scroll down within Sequence QC options to Header fields. The default header template is {sample}|{location}|{date}.' %}

{% include question.html content='Think back to our exploration of the provided metadata files. Will this template match up with our metadata?' %}
{% include tip.html content='look at the column headers' %}

   {% include question.html content='Given three alternative templates below, rank them best → worst and justify:<br>
   1. `{sample}|{date}`<br>
   2. `{sample}|{admin1}|{admin2}|{date}`<br>
   3. `{admin2}|{date}`<br>
   4. `{sample}|{location}|{date}`
' %}

   {% include image.html file="epi2me_raccoon6.png" prefix=root_url %} <br />

{% include enum.html number='8' content='Scroll down in Sequence QC options. The default Metadata ID field is sample. Write in the location column we would like to have raccoon use.' %}

{% include question.html content='Between admin1 and admin2, which is the better choice?' %}

{% include question.html content='What would impact this choice?' %}
{% include tip.html content='think of how complete metadata may be'%} 

{% include enum.html number='9' content='We will leave Alignment QC Options, Tree QC Options, Output Options and Nextflow configuration as default. Feel free to explore configuration options.' %}

{% include image.html file="epi2me_raccoon7.png" prefix=root_url %} <br />

{% include enum.html number='10' content='To Launch the workflow, click Launch workflow in the bottom right corner. A window should pop up. Click Launch to start the pipeline.' %}

{% include image.html file="epi2me_raccoon8.png" prefix=root_url %} <br />

{% include enum.html number='11' content='The pipeline will begin running and you can monitor the progress of each step.' %}

{% include image.html file="epi2me_raccoon9.png" prefix=root_url %} <br />

{% include enum.html number='12' content='When the pipeline successfully runs all steps, you will see the progress status change from Running to Completed.' %}

{% include image.html file="epi2me_raccoon10.png" prefix=root_url %} <br />

{% include enum.html number='13' content='If the Running status does not change to Completed and instead turns red and changes to Stopped With Error, something has gone wrong. The ability to read and interpret error messages is the most useful skill for any bioinformatician. If you see this message, navigate to the Logs menu.' %}

{% include image.html file="epi2me_raccoon11.png" prefix=root_url %} <br />

{% include enum.html number='14' content='The Logs window shows the output from Nextflow as it runs and any error messages will show at the bottom. This log can look intimidating, but it contains useful information! If you have an error, scroll down to the bottom. Can you identify the error message?' %}
{% include tip.html content='it often is printed following the word `ERROR`' %}

{% include image.html file="epi2me_raccoon12.png" prefix=root_url %} <br />


{% include enum.html number='15' content='In this example, the error reads: ERROR: Field location in header template not found in metadata columns: admin1, sample, date, admin2, admin0, travel history, notes' %}

{% include question.html content='What does that suggest went wrong during this pipeline run?' %}

{% include question.html content='How would you solve this error when you run the pipeline next time?' %} 

**Checkpoint questions:**
- What criteria are used to filter sequences?
- If our metadata file contained the following columns – ID, country, health_zone, sample_date – what would an appropriate header fields template be? 
- Where can you find information that can help explain an error?


---

## 4. Interpreting the output of raccoon-nf (seq-qc)

### Concepts to cover
- ID matching between sequence headers and metadata table rows
- Harmonising metadata from multiple files
- Preserving epidemiologically useful fields in headers

### Steps

{% include enum.html number='1' content='Navigate to the Reports tab.' %}

   {% include image.html file="epi2me_output1.png" prefix=root_url %} <br />

{% include enum.html number='2' content='Click on execution_report.... dropdown to view the available reports. Select seq-qc_report.html to open the seq-qc report.' %}

   {% include image.html file="epi2me_output2.png" prefix=root_url %} <br />

{% include enum.html number='3' content='Explore the seq-qc sections in turn.' %} 

The report summary section provides an overview of the data including total sequences, the date range associated with the sequence metadata and any filters applied. 

{% include question.html content='How many sequences were detected in the two files?' %} 


The inputs files section describes the FASTA and metadata files loaded into raccoon, with an overview of the number, length and ambiguous base content of the sequences in the input FASTA files. Click to expand each file to view QC information for each sequence. 

The sequence length distribution plot shows lengths of the sequences in the input FASTA files. 

{% include question.html content='Are there any outliers in terms of sequence length?' %}

The metadata description plot summarises the geographical and temporal distribution of the dataset provided. 

{% include question.html content='When was the earliest sequence sampled?' %}

{% include question.html content='How many unique admin2 locations are included in the dataset?' %} 

The filtered sequences table highlights sequences flagged for filtering during the QC check.

{% include question.html content='Were there any sequences filtered out? Why were they filtered?' %}

{% include question.html content='What is the shortest sequence? Why do we not want to include a short sequence?' %}

{% include question.html content='What sequence has the highest N content?' %} 


The final dataset table describes the final, combined dataset, with harmonised headers.

{% include question.html content='How many sequences are included in the final dataset?' %}


Finally, any metadata issues such as missing fields or inability to match sequences are flagged in the metadata issues table.

{% include question.html content='Are there any sequences with missing metadata fields? How has raccoon handled these?' %}

### Discussion
- Is it better to relax `--max-n-content` or drop marginal sequences? Why?
- What are the risks of including poor-quality but epidemiologically important samples?


## 4. Interpreting the output of raccoon-nf (aln-qc)

### Concepts to cover
- The impact of high N content on downstream phylogenetic inference
- The importance of visually inspecting your alignment

### Steps


{% include image.html file="epi2me_output3.png" prefix=root_url %} <br />

{% include enum.html number='1' content='Next, open the aln-qc report by clicking on the html dropdown. Explore the different sections. Prior to any phylogenetic analysis, it is necessary to inspect the input alignment to assess its quality. Raccoon can help highlight parts of the alignment to investigate further. This is an important step before we start to build our tree, since alignment issues can significantly change the tree structure and our confidence in our conclusions.' %}

{% include enum.html number='2' content='The summary provides an overview of the multiple sequence alignment, including the number of sequences, alignment length and N content.' %}

{% include enum.html number='3' content='The alignment N-content section provides a more detailed picture of what parts of the alignment contain ambiguous bases.' %}

{% include question.html content='Are there long stretches of Ns in our sequence?' %}

{% include question.html content='What effect might this have on our downstream analysis?' %}

{% include enum.html number='4' content='If specific sites have been identified by raccoon as possibly problematic, they will be reported in the flagged sites section. The table shows sites identified, sequences they were found in, and their location. The note column explains why each site was flagged.' %}

{% include question.html content='How many sites have been flagged?' %}

{% include question.html content='Why were they identified as problematic? What biological vs technical explanation is plausible?' %}

{% include question.html content='If more than one sequence contains the flagged SNP, is this SNP more or less likely to be biological?' %}

{% include enum.html number='5' content='These sites are not necessarily problematic, but investigate the alignment quality. These are good places to visually inspect. If a sequence has more than 20 sites flagged, that sequence will be flagged for removal.' %}

{% include question.html content='Have any sequences been flagged for removal?' %}

{% include enum.html number='6' content='The diversity plot allows us to see how conserved or variable sites are across the alignment, possibly flagging alignment issues.' %}

{% include image.html file="alignment.png" prefix=root_url %} <br />

{% include enum.html number='7' content='Next we will open the alignment file in Sealion to investigate the flagged sites. In EPI2ME, navigate to the Files tab. Then click into raccoon_tutorial_data > then mafft to see the aligned FASTA file.' %}

{% include enum.html number='8' content='To open the directory to access the alignment file, click the three dots and select Open in Finder or Open folder, depending on your platform. A file browser window will show where the alignment file is located.' %}

{% include image.html file="sealion.png" prefix=root_url %} <br />

{% include enum.html number='9' content='In a web browser window, navigate to artic-network.github.io/sealion/. Drag and drop your alignment file in to explore your alignment.' %}

{% include image.html file="sealion2.png" prefix=root_url %} <br />

{% include enum.html number='10' content='Use the flagged sites as a guide to assess the quality of your alignment.' %} 

{% include question.html content='Notice the Ns present at the start and end of the alignment in the latest sequence data. What might give rise to this?' %}

{% include image.html file="sealion3.png" prefix=root_url %} <br />

{% include enum.html number='11' content='Sealion can be used to view amino acid translation of coding sequences in different reading frames (Click Show > Amino Acids). Explore the different reading frames to investigate what the genome codes for.' %}

{% include question.html content='Can you decipher the code?' %}


## 4. Interpreting the output of raccoon-nf (tree-qc)

### Concepts to cover
- How to read a phylogenetic tree
- Interpreting a root-to-tip plot

### Steps


   {% include image.html file="epi2me_output4.png" prefix=root_url %} <br />

{% include enum.html number='1' content='Once the tree has been built, raccoon-nf conducts further QC checks and produces a report. Open the tree-qc_report.html in the EPI2ME browser. The summary provides overview information about the tree. Navigate to the Interactive tree section. Tips can be colored according to various traits.' %}

{% include enum.html number='2' content='Colour the tips by year, then colour the tips by location.' %}

   {% include question.html content='Do the samples cluster by location and time?' %}

   {% include question.html content='What is the closest historical sequence to our newly generated sequences?' %}

   {% include question.html content='What does the historical context add to the interpretation, and what conclusions would be different if only the case sequences were analysed?' %}

   {% include image.html file="peartree.png" prefix=root_url %} <br />

{% include enum.html number='3' content='Open and view this phylogeny in PearTree.' %}

   {% include question.html content='Can you locate the treefile in the output Files? Refer to the instructions for finding the alignment file.' %} 
   {% include tip.html content='look under `tree` and identify the `.treefile` file.' %}

{% include enum.html number='4' content='Inspect the phylogeny, click the visual settings button in the top right corner to open the panel, and turn on tip labels to show names and explore where the newly generated sequences lie within the known diversity.' %}

   {% include question.html content='Do the samples cluster by location and time?' %}

   {% include question.html content='Are *all* newly generated sequences clustering together?' %}

   {% include question.html content='Describe what the phylogeny tells us about sample PHL036? ' %}
   
   {% include tip.html content='(In the top right text box, type in PHL036 to locate the tip)' %}

   {% include question.html content='What does the phylogeny tell us about sample PHL043?' %}

{% include enum.html number='5' content='Compare the epidemiological information provided in the metadata with the structure of the phylogeny.' %} 

{% include question.html content='Are the clusters consistent with the epi-links?' %} 

{% include enum.html number='6' content='The Root-to-tip regression plots each tip according to its sampling date and its distance from the root of the tree. The regression line is also plotted, estimating the overall molecular clock of the dataset.' %}

{% include question.html content='Do most of the recent samples fall along the regression line?' %}

{% include question.html content='Are there any outliers? What does the root-to-tip plot say about sample PHL036?' %}

{% include question.html content='What possible causes could give rise to this?' %}

{% include enum.html number='7' content='If an outgroup had been selected in our raccoon-nf run, ancestral state reconstruction would have been performed and additional QC checks. We have not performed this analysis in this tutorial.' %}

{% include enum.html number='8' content='Now that we have explored the output phylogeny, there are next steps we could take. We have identified outliers and unrelated cases which we would want to remove prior to running further temporal analysis using Bayesian methods in software such as BEAST. We will not be running temporal analysis today, but you are now in a good position to do additional downstream analysis.' %}


---

## Discussion

{% include question.html content='What challenges did you encounter during the workflow? Did you encounter any errors during execution?' %} 

{% include question.html content='How would you adapt this workflow for a different virus or dataset?' %} 
{% include tip.html content='Think of read length, header fields and sourcing background data.' %}

---

## Additional Resources

- [Raccoon Documentation](https://github.com/artic-network/raccoon)
- [MAFFT Manual](https://mafft.cbrc.jp/alignment/software/)
- [IQTREE Documentation](http://www.iqtree.org/doc/)
- [BEAST website](https://beast.community/)

---

### Software used in raccoon-nf

- [Raccoon](https://github.com/artic-network/raccoon)
- [MAFFT](https://mafft.cbrc.jp/alignment/software/)
- [IQTREE](http://www.iqtree.org/doc/)
- [jclusterfunk](https://github.com/rob-p/jclusterfunk)

## Attribution

This tutorial is intended for both:

- workshop delivery (guided teaching)
- self-paced reference for raccoon users
