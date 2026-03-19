---
id: alcohols-amines
title: "Improve parameters for alcohols and amines"
category: accuracy
recommended: true
stages:
  - data_generation
  - fitting
  - benchmarking
  - release
summary: "Refit and release an OpenFF force field with improved accuracy for alcohol and amine functional groups."
fte:
  infrastructure: 0
  science_code: 0
  science_exp: 6
timeline:
  - milestone: "Proof-of-concept fit with alternative alcohol electrostatics complete"
    date: "Q3 2026"
  - milestone: "Force field re-fitting complete, with multiple iterations"
    date: "Q4 2026"
  - milestone: "Benchmarking complete"
    date: "Q1 2027"
  - milestone: "Candidate period and release"
    date: "Q2 2027"
metrics:
  - "Physical properties improved for alcohols and amines"
  - "SFEs improved for alcohols and amines"
  - "No regressions across other chemical classes (full Sage benchmark suite passes)"
go_no_go:
  - gate: "Q3 2026"
    condition: "Root cause and possible fixes for alcohol/amine errors identified. If systematic re-fit of electrostatics or virtual sites required, prioritize Neural Network Charges or Virtual Sites"
dependencies: []
enables: []
---

## Goals

- Perform systematic error analysis on the performance of current Sage 2.x parameters for alcohols and amines, specifically targeting hydration free energies and conformational torsion profiles
- Identify the specific SMIRKS patterns, torsion dihedral types, and charge model assignments responsible for the largest errors
- Generate targeted QM datasets to fill identified gaps: high-level torsion scans for under-represented OH and NH dihedral types, and extended ESP datasets for partial charge improvement
- Refit the relevant SMIRNOFF torsion and Lennard-Jones parameters using the augmented dataset
- Release as an update to the Sage force field line

## Benefits

Alcohols and amines together represent approximately 60% of drug-like molecules with heteroatom functionality. Known systematic errors in hydration free energies for primary and secondary amines, and in conformational preferences for some alcohol geometries, directly impact binding affinity predictions across a large fraction of drug discovery applications.

A targeted data-and-fitting approach is more robust than ad-hoc fixes: it addresses the underlying causes of errors rather than patching individual failure cases. The methodology established here also provides a template for applying similar targeted improvements to other functional group classes in future development cycles.
