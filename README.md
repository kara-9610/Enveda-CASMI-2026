# Enveda-CASMI-2026

## Overview

### Purpose
Help uncover the chemical diversity of nature.  
To build models that predict natural product structures from mass spectra.

### Description
Modern mass spectrometry can detect thousands of molecules in nature, but identifying them all remains a challenge.  
Current method mostly compare spectra against reference libraries. They work for known compounds but struggle with the many unknown molecules found in real biological samples.  
In this competition, you'll build machine learning models that predict 2D chemical structures (a SMILES string) from LC-MS/MS spectra. Your goal is to generate accurate SMILES representations for both **known** and **novel** molecules.

### Background
**What is an MS/MS mass spectrum?**  

- **Ionization**: The instrument can only detect and measure charged ions, so first a molecule is ionized, picking up or losing charged species. In the instrument's **positive ion mode** (more common for small molecules), the resulting ion is positively charged, in **negative ion mode** (less common but still used), it is negatively charged. The kind of charged ion the molecule acquires is called an **adduct**. For some common examples, the molecule may acquire a proton (positive), acquire an ammonium ion (positive), or lose a proton (negative). We would write these adduct forms respectively as [M+H]+, [M+NH4]+, or [M-H]-.

- **Precursor mass detection**: The instrument measures the ion's **precursor m/z** (mass-to-charge ratio) with high accuracy, which strongly constrains the molecular formula. For small molecules, the charge (z) is usually +1 or -1, so m/z corresponds to the mass of the ion, and sometimes we will refer to m/z simply as "mass".

- **Fragmentation**: The precursor ion (actually many individual ions of the same molecule+adduct) is then selected and fragmented by collision with neutral gas at a given **collision energy**, and the instrument records the **m/z and intensity (abundance) of each fragment**. The histogram of intensities across all detected fragments is the molecule's mass spectrum. Intensities are typically normalized. Each m/z is called a **fragment ion or peak** (peaks of individual fragment ions), the **base peak** (highest-intensity fragment ion), the **precursor peak** (m/z corresponding to the intact, unfragmented ion). It may or may not be present, depending on how thoroughly the ion was fragmented.

### Evaluation
Submissions are evaluated using Mean Reciprocal Rank @ 25 (MRR@25):

$$
\text{MRR@25} = \frac{1}{U} \sum_{u=1}^{U} \frac{1}{\text{rank}_u}
$$

