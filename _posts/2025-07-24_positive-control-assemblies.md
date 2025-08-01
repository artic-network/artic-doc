---
title:  "Genome assemblies for a respiratory metagenomics positive control"
published: true
permalink: 2025-07-26_positive-control-genome-assemblies.html
tags: [news]
author: Bede Constantinides
---

Clinical metagenomics uses complex laboratory protocols to detect DNA and RNA from viral and bacterial pathogens. For best results, different sample types—from viscous sputum to blood with high host background—demand specific handling. For reliable routine diagnostics, these methods must detect pathogens both sensitively and precisely, demanding robust control specimens and validation procedures.

Negative controls are relatively straightforward: one can process a mock sample containing pure water or a negative sample matrix alongside real specimens, and monitor the resulting sequences for artifacts caused by contamination, barcode hopping or otherwise. Positive controls are more challenging: an ideal positive control specimen would comprise known quantities of various pathogen taxa anticipated to be found in tested specimens, as well as a high host background to mimic real samples. But culturing and maintaining such a stock of live pathogens is laborious, expensive, and unlikely to yield reproducible results after shipping and storage.

ZeptoMetrix® sells a variety of controls for diagnostic validation purposes. Their NATtrol™ Respiratory Panel 2.1 (RP2.1) reportedly contains "purified, intact bacterial cells and viral particles" that are "chemically modified to render them non-infectious and refrigerator stable". The RP2.1 panel is marketed as containing 18 complete viral and 4 bacterial taxa including *Bordetella* spp., influenza viruses, coronaviruses, and adenoviruses, split into two subpanels. Albeit advertised as qualitative rather than quantitative, it is a promising commercially available control specimen for respiratory metagenomics.

ZeptoMetrix® provides a [datasheet](https://www.zeptometrix.com/us/en/nattrol-respiratory-panel-21-rp21-controls-12-x-03ml-3084) documenting the strains included in the each RP2.1 subpanel, yet does not disclose genome sequences. As part of evaluation of the RP2.1 panel by researchers from the ARTIC network at the University of Birmingham, we have released draft quality nanopore assemblies for 16/18 virus genomes contained in RP2.1 with \>90% coverage. These [consensus assemblies are publicly available](https://github.com/bede/zmrp) and [archived on Zenodo](https://zenodo.org/records/16412857). We have also developed a simple [workflow for rapidly estimating sequencing coverage](https://github.com/bede/knownknowns) of RP2.1—or any other references—using *k*\-mer containment with [Sourmash](https://joss.theoj.org/papers/10.21105/joss.06830).

**Lab methods**

Typically, viral metagenomic sequencing directly from clinical samples results in poor sensitivity due to large host backgrounds and low viral abundance. To enrich for the viruses described in the Zeptometrix control, an adapted version of the [Oxford Nanopore Technologies (ONT) Rapid Metagenomic Sequencing protocol](https://nanoporetech.com/document/rapid-sequencing-metagenomics-sqk-rpb114-24#overview-of-protocol) following the viral sample preparation arm was used. This method is based on a SMART (Switching Mechanism at the 5′ end of RNA Template) approach and uses random priming for cDNA synthesis followed by PCR amplification using ONT rapid barcodes to amplify and barcode cDNA in a single step. The resulting libraries were sequenced on the ONT PromethION (R10.4.1) to generate sufficient data for assembling the RP2.1 panel genomes.

**Informatic methods**

ONT PromethION reads were basecalled with model version 4.3.0 HAC. Initial reference sequences were selected using strain information provided in the panel’s [datasheet](https://web-resources-prod.zeptometrix.com/documents/public/PI/PINATRPC2.1-BIO.pdf). Consensus sequences were generated using [Minimap2](https://github.com/lh3/minimap2) `-x map-ont` and [Kindel](http://github.com/bede/kindel) prior to polishing with [Dorado](https://github.com/nanoporetech/dorado).



**Draft genomes**: [github.com/bede/zmrp](https://github.com/bede/zmrp)

**Containment estimation workflow**: [github.com/bede/knownknowns](https://github.com/bede/knownknowns)



| Genome                              | Abbreviation | Reference   | Type | Length | Assembled |
| ----------------------------------- | ------------ | ----------- | ---- | ------ | --------- |
| Adenovirus Type 1                   | AdV-1        | AC_000017.1 | DNA  | 35,676 | ✅         |
| Adenovirus Type 3                   | AdV-B        | DQ099432.4  | DNA  | 35,072 | ✅         |
| Adenovirus Type 31                  | AdV-31       | AM749299.1  | DNA  | 33,755 | ✅         |
| Influenza A H1N1 A/NY/02/2009       | Flu-A-H1N1-S | KT180555.1  | RNA  | 13,130 | ✅         |
| Influenza A H3N2 A/Brisbane/10/07   | Flu-A-H3N2   | KJ609211.1  | RNA  | 13,290 | ✅         |
| Influenza AH1 A/New Caledonia/20/99 | Flu-A-H1N1-F | CY033629.1  | RNA  | 13,292 | ✅         |
| Influenza B B/Florida/02/06         | Flu-B        | CY018371.1  | RNA  | 14,222 | ✅         |
| Metapneumovirus 8 Peru6-2003        | HMPV         | OL794390.1  | RNA  | 13,149 | ✅         |
| Parainfluenza Type 1                | HPIV-1       | PV660323.1  | RNA  | 15,412 | ✅         |
| Parainfluenza Type 2                | HPIV-2       | AF533012.1  | RNA  | 15,654 | ✅         |
| Parainfluenza Type 3                | HPIV-3       | KY674922.1  | RNA  | 15,382 | ✅         |
| Parainfluenza Type 4                | HPIV-4       | EU627591.1  | RNA  | 17,132 | ⚠️ gaps    |
| Rhinovirus 1A                       | HRV-1A       | KC894166.1  | RNA  | 7,096  | ✅         |
| RSV A                               | RSV-A        | KY967364.1  | RNA  | 14,855 | ✅         |
| SARS-CoV-2 USA-WA1/2020             | SARS-CoV-2   | ON311149.1  | RNA  | 29,778 | ✅         |
| Coronavirus 229E                    | HCoV-229E    | OZ035244.1  | RNA  | 26,841 | ✅         |


{% include links.html %}
