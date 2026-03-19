---
id: toolkit-refactor
title: "Refactor OpenFF Toolkit"
category: infrastructure
recommended: false
stages:
  - infra_updates
summary: "Consolidate the OpenFF Toolkit and Interchange, move to an RDKit-only backend, remove bond order and charge storage from the Toolkit, and add a tensor representation for direct translation to smee — reducing maintenance burden and aligning the Toolkit with the modern fitting stack."
fte:
  infrastructure: 3
  science_code: 0
  science_exp: 0
timeline:
metrics:
go_no_go:
dependencies: []
enables: []
---

## Goals
- integrate repos into a mono-repo
- remove bond orders and charge from Molecule representation

## Benefits

