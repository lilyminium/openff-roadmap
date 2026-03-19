---
id: virtual-sites
title: "Virtual sites"
category: accuracy
recommended: true
stages:
  - data_generation
  - fitting
  - benchmarking
  - release
summary: "Develop and release a SMIRNOFF force field incorporating virtual sites to better capture sigma holes, lone pairs on nitrogen, and other anisotropic electrostatic features."
fte:
  infrastructure: 0.5
  science_code: 1
  science_exp: 6
timeline:
  - milestone: "Virtual site SMIRNOFF infrastructure validated in smee/descent"
    date: "Q3 2026"
  - milestone: "First complete virtual site force field fit complete"
    date: "Q4 2026"
  - milestone: "Benchmarking"
    date: "Q1 2027"
metrics:
  - "Improved treatment of ESP"
  - "Improved dimer profiles"
  - "Physical property benchmarks not worsened"
go_no_go:
  - gate: "Q1 2027"
    condition: "Virtual site force field does not degrade benchmarks; otherwise, reassess approach"
dependencies:
  - smee-descent
enables: []
---

## Goals

- A prototype virtual site force field addressing sigma holes and pyridine lone pair without worse performnance on physical properties

## Benefits

Virtual sites allow more complex treatments of electrostatic interactions.
