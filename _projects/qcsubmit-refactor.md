---
id: qcsubmit-refactor
title: "Refactor and simplify QCSubmit"
category: infrastructure
recommended: true
stages:
  - infra_updates
summary: "Refactor QCSubmit to reduce maintenance burden and make it fit for purpose as a daily tool for OpenFF scientists"
fte:
  infrastructure: 0.5
  science_code: 0
  science_exp: 0
timeline:
  - milestone: "Audit complete; pain points catalogued; deprecation plan agreed with team and communicated to external users"
    date: "Q3 2026"
  - milestone: "Refactored QCSubmit released with streamlined API"
    date: "Q4 2026"
metrics:
  - "Scientific workflows can practically use QCSubmit instead of converting to a different format at the earliest opportunity"
go_no_go:
dependencies: []
enables: []
---

## Goals

- Audit QCSubmit codebase for redundancy and pain points
- Fix these

## Benefits

**The primary benefit is reduced maintenance burden.** QCSubmit has accumulated substantial legacy functionality — dataset types from defunct workflows, compatibility layers for old QCFractal APIs, and abstraction layers that add complexity without adding value.

**QCSubmit is not currently serving the needs of OpenFF scientists well.** The existing API is slow and painful to use, especially with regards to the smee software stack, where some hacks need to be made to download torsiondrives with speed.
