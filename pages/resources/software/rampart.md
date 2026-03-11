---
title: RAMPART
title_text: "RAMPART"
subtitle_text: "Read Assignment, Mapping, and Phylogenetic Analysis in Real Time."
image: /images/software/rampart-icon.png
summary: "RAMPART runs concurrently with MinKNOW and provides a real-time overview of virus genome coverage and reference matching for each barcode, enabling informed decisions during sequencing runs."
sidebar: artic_sidebar
permalink: /software/rampart
icon: /images/software/rampart-icon.png
folder: software
keywords: resources
tags: [resources, software]
---

RAMPART (**R**ead **A**ssignment, **M**apping, and **P**hylogenetic **A**nalysis in **R**eal **T**ime) runs concurrently with MinKNOW and shows you demultiplexing and mapping results as reads come off the sequencer. It provides a real-time overview of genome coverage and reference matching for each barcode, making it possible to make informed decisions about sequencing runs while they are still in progress.

RAMPART was originally designed to work with amplicon-based primer schemes (e.g. for Ebola virus), but this is not a requirement. It can be adapted to any ONT sequencing workflow via configurable protocols.

## Desktop app

RAMPART is now available as a self-contained **Electron desktop application** for macOS and Windows. The app bundles the Node.js server, React frontend, and all dependencies, so no separate server setup is needed.

Pre-built installers for the latest release can be downloaded from the **[GitHub Releases page](https://github.com/artic-network/rampart-app/releases)**:

| Platform | Installer |
|----------|-----------|
| macOS — Apple Silicon (M1/M2/M3/M4) | `RAMPART.1.3.x_aarch64.dmg` |
| macOS — Intel (x86-64) | `RAMPART.1.3.x_x64.dmg` |
| Windows | `RAMPART.1.3.x_x64-setup.exe` |
| Linux (Debian/Ubuntu) | `artic-rampart_1.3.0_amd64.deb` |
| Linux (AppImage) | `RAMPART-1.3.0.AppImage` |

## Documentation

- [Installation](https://github.com/artic-network/rampart-app/blob/main/docs/installation.md)
- [Running an example dataset & understanding the visualisations](https://github.com/artic-network/rampart-app/blob/main/docs/examples.md)
- [Setting up for your own run](https://github.com/artic-network/rampart-app/blob/main/docs/setting-up.md)
- [Configuring RAMPART using protocols](https://github.com/artic-network/rampart-app/blob/main/docs/protocols.md)
- [Debugging when things do not work](https://github.com/artic-network/rampart-app/blob/main/docs/debugging.md)
- [Notes relating to RAMPART development](https://github.com/artic-network/rampart-app/blob/main/docs/developing.md)

## Source code & issues

RAMPART is open-source software (GPL-3.0). Source code and issue tracker are on GitHub:
[https://github.com/artic-network/rampart-app](https://github.com/artic-network/rampart-app)

{% include links.html %}
