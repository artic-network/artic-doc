---
title: PearTree
title_text: "PearTree"
subtitle_text: "Phylogenetic Tree Viewer and Explorer."
image: /images/software/peartree-icon.png
summary: "PearTree is a fast, interactive phylogenetic tree viewer for NEXUS and Newick trees, with annotation colouring, a time-calibrated axis, subtree navigation, and publication-quality SVG/PNG export."
sidebar: artic_sidebar
permalink: /software/peartree
icon: /images/software/peartree-icon.png
folder: software
keywords: resources
tags: [resources, software]
---

PearTree is a fast, interactive phylogenetic tree viewer designed for genomic epidemiology. It can display large NEXUS and Newick trees with rich visual controls, colour branches and tips by any annotation, show a time-calibrated axis, and export publication-quality SVG or PNG figures.

## Using PearTree

### Web app

The easiest way to use PearTree is directly in your browser — no installation required:

**[https://artic-network.github.io/peartree](https://artic-network.github.io/peartree)**

Drag and drop a NEXUS or Newick tree file onto the canvas, or use the **Open…** button. You can also load example data or point the app at a tree file URL. 

### Desktop app

A native desktop application is available for macOS, Windows, and Linux, built with [Tauri](https://tauri.app/). It offers the same features as the web app with native file system access and the ability to open FASTA files directly from your file manager.

Pre-built installers for the latest release can be downloaded from the **[GitHub Releases page](https://github.com/artic-network/peartree/releases)**:

| Platform | Installer |
|----------|-----------|
| macOS — Apple Silicon (M1/M2/M3/M4) | `PearTree_x.x.x_aarch64.dmg` |
| macOS — Intel (x86-64) | `PearTree_x.x.x_x64.dmg` |
| Windows | `PearTree_x.x.x_x64-setup.exe` |
| Linux (Debian/Ubuntu) | `peartree_x.x.x_amd64.deb` |
| Linux (AppImage) | `peartree_x.x.x_amd64.AppImage` |

## Key features

- **Annotation colouring** — colour tip labels, tip shapes, and internal nodes by any annotation field loaded from the tree or imported from a CSV/TSV file; categorical and continuous colour palettes supported
- **Hyperbolic lens** — expand a region of a large tree to label-readable spacing without losing sight of the rest
- **Subtree navigation** — double-click any node to drill down into its clade; navigate back and forward through your view history
- **Time-calibrated axis** — calibrate using a date annotation, then display a calendar-date axis with configurable major/minor tick intervals
- **Import annotations** — load per-tip metadata from a CSV or TSV file and map it to any annotation field in the tree
- **Hide/show subtrees** — remove nodes and clades from the view to focus on subsets of interest
- **Branch ordering and rotation** — sort clades by size ascending or descending, or rotate individual nodes
- **Export tree** — save as NEXUS (with embedded visual settings) or Newick; choose entire tree or current subtree view
- **Export graphic** — export the current view or full tree as SVG (vector) or PNG (2× raster)
- **BEAST tree support** — displays node height HPD bars and recognises posterior probability and other annotations from BEAST output

## Source code & issues

PearTree is open-source software. Source code and issue tracker are on GitHub:
[https://github.com/artic-network/peartree](https://github.com/artic-network/peartree)

{% include links.html %}
