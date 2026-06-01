---
title: "Bundibugyo virus genomic sequencing resources"
keywords: protocol
layout: document
tags: [protocol] 
permalink: /viruses/bdbv/bdbv-sequencing-guide.html
folder: bdbv
title_text: "Bundibugyo virus genomic sequencing resources"
subtitle_text: "A guide to sequencing for genomic epidemiology"
document_name: "ARTIC-BDBV-sequencing-guide"
version: v1.0.0
creation_date: 2026-05-28
last_updated: 2026-05-28
author: ARTIC team
category: guide
order: 2
---

## Initial sequencing results

The results of initial sequencing from the 2026 epidemic of Bundibugyo virus were reported jointly by Institut National de Recherche Biomédicale (INRB) in DRC and Central Public Health Laboratory (CPHL) in Uganda via a post on [Virological](https://virological.org/t/initial-genomes-from-may-2026-bundibugyo-virus-disease-outbreak-in-the-democratic-republic-of-the-congo-and-uganda/1032), with subsequent updates as new genome data has been generated. Sequence data is published through [Pathoplexus](https://pathoplexus.org/).

Timely release of genome sequencing data is important for the validation of diagnostic tests, to inform vaccine and therapeutic candidates, and for epidemiological inferences including source attribution. Initial analysis of sequences have indicated that the Bundibugyo virus (BDBV) epidemic is a new spillover event from a zoonotic reservoir. Early analysis (subject to change as more genomes are sequenced) indicates that the time to the most recent common ancestor, an approximate estimate of the beginning of the outbreak, lies between late March and late April. However, all the genomes at the time of writing are from or linked to Bunia so this may not be representative of the epidemic as a whole.

At present there are too limited a number of genomes to infer (from genomes) other epidemic parameters including epidemic size, R0 and the number of chains of transmission.

In this briefing document, we aim to summarise the currently available knowledge of technical approaches for the sequencing of Bundibugyo genomes and downstream analysis for laboratories engaged in Ebolavirus genomics.

## Sequencing protocols

*Bait capture*

Initial genomes have been sequenced with [Twist Comprehensive Viral Panel](https://www.twistbioscience.com/products/ngs/fixed-panels/comprehensive-viral-research-panel) (DRC) or Illumina Viral Surveillance Panel V2 (Uganda) and Illumina sequencing which has generated reliable sequencing results with high coverage (\>99%) from samples with Cts ranging between 17-25.  This approach, whilst effective, is expensive to run at scale due to the high costs of the bait capture kit.

Other bait capture kits may also be effective for sequencing, but it should be confirmed that the panel includes bait probes for BDBV as notably some viral panels do not, for example it was added to version 2 of the Illumina Viral Surveillance Panel.

*Amplicon panels*

The ARTIC pan-Ebola v1.0 primer scheme, [artic-pan-ebola/1000/v1.0.0](https://labs.primalscheme.com/detail/artic-pan-ebola/1000/v1.0.0/?q=ebov), has been tested by a number of partners (DRC, Bernard Nocht) and generates around 50-70% genome coverage on testing so far with the BDBV epidemic strain. Although such genomes can be useful for positive sequence identification of diagnostically ambiguous samples and broad lineage typing, the coverage is too low to be recommended for routine sequencing e.g. for genomic epidemiology early on where it is important to capture all the mutations present in the genome.

*Updates to amplicon panels*

ARTIC have subsequently designed an updated pan-Ebola scheme, artic-pan-ebola/1000/v2.0.0, as well as a BDBV specific scheme, [artic-bdbv-2026/400/v1.0.0](https://labs.primalscheme.com/detail/artic-bdbv-2026/400/v1.0.0/?q=ebov), incorporating the BDBV sequence from this epidemic to ensure a more specific panel and improve genome sequence coverage. The design will be made available through [Primal Scheme Labs](https://labs.primalscheme.com/) and is currently being synthesised for pooling and distribution through the ARTIC Primer Foundry. Both schemes are freely available on request and ARTIC will cover the shipping costs. We anticipate the BDBV specific scheme will generate the best results for a variety of sample inputs. In keeping with other ARTIC protocols, it will work on Illumina and ONT platforms and will be able to generate large numbers of sequences per sequencing run (96-384 depending on library kit) from samples with a broad range of viral titres. Validation will be carried out at INRB.

*Metagenomics*

ARTIC have not heard any reports of metagenomics approaches being used to sequence BDBV in this epidemic yet but this should be an appropriate method for samples with low Ct (recommended \<20, although genomes may be recovered between 20-30 in some cases depending on the level of host background). We would recommend the [SMART-9N](https://www.protocols.io/view/viral-metagenomics-using-smart-9n-amplification-an-j8nlke5wwl5r/v1) or other SISPA-based protocols for this as it is optimised for viral RNA recovery. Metagenomics approaches might be useful for groups that do not yet have access to bait or amplicon panels. SMART-9N primers can be supplied on request. Metagenomics may be an important assay when there is diagnostic uncertainty in case of the emergence of other strains of Ebolavirus or other haemorrhagic fevers during the course of the epidemic.

## Bioinformatics protocols

*TWIST bait capture bioinformatics*

For Twist viral capture panel results, INRB reported good results with [nf-core/viralrecon](https://github.com/nf-core/viralrecon). Bait capture data on Illumina at high coverage can be assembled *de novo* assembly using standard methods such as metaSpades or MEGAHIT.

*Amplicon Sequencing bioinformatics*

We recommend the [artic-network/amplicon-nf](https://github.com/artic-network/amplicon-nf) pipeline for both ONT and Illumina amplicon sequencing, tutorials on using the pipeline are available on the [artic website](https://artic.network/resources/amplicon-nf) and the [amplicon-nf github repository](https://github.com/artic-network/amplicon-nf/tree/main/docs). We recommend using a BDBV epidemic reference strain as the reference for variant calling, please [refer to the ARTIC website](https://artic.network) for further details.

## Phylogenetics

Standard phylogenetic approaches work well for BDBV including multiple alignment with [MAFFT](https://mafft.cbrc.jp/alignment/software/) and phylogenetic tree building with [IQ-TREE](https://iqtree.github.io) \- the number of genomes isexpected to remain well within the practical limits for these tools for the immediate future. 

We offer an integrated software package, raccoon – [https://github.com/artic-network/raccoon](https://github.com/artic-network/raccoon) that combines these steps along with sequence, alignment and phylogenetic QC and generates HTML reports. Raccoon can be run independently or as a NextFlow pipeline from [https://github.com/artic-network/raccoon-nf](https://github.com/artic-network/raccoon-nf) and the latter can be run within ONT’s EPI2ME desktop software without need for command-line experience. A step-by-step tutorial and description of output files can be found at https://artic.network/tutorials/raccoon-nf.html.

Further tree interpretation can be performed with PearTree (desktop apps available from [http://github.com/artic-network/peartree](http://github.com/artic-network/peartree) or a zero-install web application at [http://peartree.live](https://peartree.live)). Genomes submitted to Pathoplexus (see below) will automatically be included in regular NextStrain updates at [https://nextstrain.org/ebola/bdbv](https://nextstrain.org/ebola/bdbv). 

Key phylodynamic and genomic epidemiology questions can be answered by software packages that generate time-calibrated trees. The pipeline that generates the tree for NextStrain uses TreeTime [https://github.com/neherlab/treetime](https://github.com/neherlab/treetime). This allows a simple estimate of the time of the most recent common ancestor (TMRCA) of the sample of genomes. A TMRCA acts as an upper bound for when the outbreak started (jumped from the reservoir into the first human). 

For more comprehensive analysis we recommend [BEAST](http://beast.community). This can provide estimates of TMRCA, epidemic growth rate, spatial spread, epidemiological parameters and more. A wide range of tutorials and documentation can be found at [http://beast.community](http://beast.community).   
   
## Data sharing via Pathoplexus

[Pathoplexus](https://pathoplexus.org/), a new online database for viral genome sequence sharing during outbreaks and epidemics, now supports Ebola Bundibugyo (BDBV) sequences. Data (metadata and associated sequences) can be submitted through the web interface or programmatically via the API (see our [How To Submit](https://pathoplexus.org/docs/how-to/upload-sequences) documentation). Country and date of sampling are required to submit, and users need to set up a [Pathoplexus account](https://pathoplexus.org/docs/how-to/create-account), and [Submitting Group](https://pathoplexus.org/docs/how-to/create-group).

Most currently available BDBV sequences have been submitted as ‘Restricted Use.’ This means:

- Sequences remain publicly accessible on Pathoplexus for viewing and download by all users  
- Data is available for all unpublished/un-preprinted analyses, especially for public health purposes (e.g. phylogenies available online, epidemiological reports, government reports) [*with proper attribution*](https://pathoplexus.org/about/terms-of-use/data-use-terms#421-unpublished-and-un-preprinted-work)  
- Use of the data **in publications or preprints** requires [either explicit permission or co-authorship](https://pathoplexus.org/about/terms-of-use/data-use-terms#422-publications-and-preprints) with the original submitting group(s), as well as proper attribution, if the data is focal to the paper (for the current BDBV outbreak, all use is considered focal)  
- Restricted-Use is time-limited for up to one year, after which the sequences become Open and are also made available on INSDC (NCBI, ENA, DDBJ)

This approach removes barriers to rapid sharing while protecting original submitters’ publication interests and ensuring proper credit.

Pathoplexus also includes all openly available BDBV sequences from INSDC (with the origin clearly attributed), allowing users to download all data in one convenient location. 

Pathoplexus augments the available sequences by providing tools such as:

- **Interactive search and filtering** \- allows exploration of sequences by geography, outbreak, collection date, metadata, and mutations  
- **Annotation and mutation calling** \- using Nextclade datasets, all sequences are annotated with appropriate genes, mutations (nucleotide and AA) are shown, and lineages/clades/outbreaks are assigned  
- **Phylogenetic analysis** \- links to the Nextstrain BDBV phylogeny and quick-placement on the Nextclade dataset reference tree  
- ‘**SeqSets**’ \- citable datasets which allow groups of sequences used to be given a unique identifier, making them easy to reference in online tools \- a DOI can also be generated, which allows tracking in publications (where use permits)  
- **INSDC integration** \- allows access to all publicly available sequences in one place, and allows direction submissions to be sent on to INSDC once they become Open

