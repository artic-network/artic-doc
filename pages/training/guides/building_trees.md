---
title: "Building phylogenetic trees for genomic epideemiology | Tutorial | Phylogenetics"
layout: document
keywords: tutorial
tags: [protocol] 
permalink: /guides/building-trees.html
title_text: "Building phylogenetic trees"
subtitle_text: "Part 3: phylogenetic trees for genomic epideemiology"
icon: /images/artic.png
document_name: "ARTIC-Tutorial-Phylogenetics-Part3"
version: v1.0.0
creation_date: 2025-08-28
last_updated: 
forked_from: 
author: Andrew Rambaut
folder: training
category: _guide
order: 3
summary: "An introduction to phylogenetic trees and how to interpret them."
---

## Overview

Building a phylogenetic tree from DNA, RNA or amino acid sequences is a inherently a statistical enterprise with the tree being an estimate of the evolutionary history of the sequenced based on a model of molecular evolution. Generally the goal is to find the tree that is the best fit to the data (the sequences) given the model. Various parameters of the model can be estimated at the same time --- e.g., the rate of evolution. The fit of the tree to the data can be assessed using a range of criteria, from simply minimising the number of mutations required to give the observed data (maximum parsimony reconstruction) to calculating the probability of observing the sequences with a detailed mathematical model of evolution (maximum likelihood and Bayesian inference). Like other types of statistical analyses we can also estimate measures of uncertainty alongside the best estimate but with phylogenetics these are not as straight-forward and are often computationally expensive (in both time and energy).    

Most phylogenetic analyses will involve the same sequence of steps with a wide range of software tools available and choices to be made for each. The general workflow will look something like this

Steps:
1) Annotating sequences with metadata
2) Align sequences
3) Choose a model of evolution
4) Build a tree
5) Rooting the tree
6) Viewing the tree
6) Diagnose issues
7) Visualise the tree for publication

## Curating sequences and annotating with metadata

Here we will assume the sequence data available are a set of genomes each isolated from a sample collected from an infected host. These are consensus genomes contructed from sequencing read,

### Naming sequences

### FASTA files

### Problem characters 

## Aligning sequences

### Alignment to a reference genome

### Multiple sequence alignment

### Pros and cons

## Choosing a model of evolution

### Missing data and ambiguities

## Building a tree

## Rooting the tree

## Diagnosing issues

Before making inferences about the tree, especially surprising or important ones, examine the tree and look for issues arising from the data, metadata or analyses choices.

### Mislabelling
(RSV subtype)
Dates etc

### Dodgy bioinformatics

### Contamination

### Recombination

### Weird shit

## Very large trees

## So we have a tree, now what?

# Time-scaled trees

