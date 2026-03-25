---
title: Sealion
title_text: "Sealion"
subtitle_text: "Sequence Alignment Viewer."
image: /images/software/sealion-icon.png
summary: "Sealion is a fast, interactive multiple sequence alignment viewer for genomic epidemiology, with genome annotation display, reference-based colouring, variable-site navigation, and amino acid translation."
sidebar: artic_sidebar
permalink: /software/sealion
icon: /images/software/sealion-icon.png
folder: software
keywords: resources
tags: [resources, software]
---

Sealion is a fast, interactive viewer for large multiple sequence alignments, designed for genomic epidemiology workflows. It can display annotated genome structure, colour sequences by nucleotide or amino acid scheme, highlight differences from a reference, and summarise variation with a per-column plot strip and an overview minimap.

## Using Sealion

### Web app

The easiest way to use Sealion is directly in your browser — no installation required:

**[https://artic-network.github.io/sealion](https://artic-network.github.io/sealion)**

Drag and drop a FASTA file onto the viewer window, or use **File → Open alignment**. Load a GenBank (`.gb`) reference genome to display annotated CDS features, colour sequences relative to the reference, and navigate between sites that differ from it.

### Desktop app

A native desktop application is available for macOS, Windows, and Linux, built with [Tauri](https://tauri.app/). It offers the same features as the web app with native file system access and the ability to open FASTA files directly from your file manager.

Pre-built installers for the latest release can be downloaded from the **[GitHub Releases page](https://github.com/artic-network/sealion/releases)**:

| Platform | Installer |
|----------|-----------|
| macOS — Apple Silicon (M1/M2/M3/M4) | `Sealion_x.x.x_aarch64.dmg` |
| macOS — Intel (x86-64) | `Sealion_x.x.x_x64.dmg` |
| Windows | `Sealion_x.x.x_x64-setup.exe` |
| Linux (Debian/Ubuntu) | `sealion_x.x.x_amd64.deb` |
| Linux (AppImage) | `sealion_x.x.x_amd64.AppImage` |

## Key features

- **Colour schemes** — several nucleotide and amino acid palettes; optionally highlight only sites that differ from the reference or consensus
- **Plot strip** — per-column conservation (entropy) or differences-from-reference bar chart
- **Overview minimap** — compressed whole-alignment view with genome structure, variable sites, and a sliding-window plot line
- **Column collapse** — compress uninformative regions to focus on variable sites
- **Sort sequences** — by name, tag, date, length, similarity to reference, or metadata from FASTA headers
- **Tags & bookmarks** — assign colour labels to sequences and mark columns for quick navigation
- **Copy as FASTA** — select a rectangular region and copy to the clipboard

## Source code & issues

Sealion is open-source software. Source code and issue tracker are on GitHub:
[https://github.com/artic-network/sealion](https://github.com/artic-network/sealion)

{% include links.html %}
