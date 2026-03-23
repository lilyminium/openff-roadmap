---
id: toolkit-refactor
title: "Refactor OpenFF Toolkit"
category: infrastructure
recommended: false
stages:
  - infra_updates
summary: "Consolidate the OpenFF Toolkit and Interchange into a single repository, move to an RDKit-only cheminformatics backend, and optionally add a tensor representation for direct translation to smee — reducing maintenance burden and simplifying the codebase."
fte:
  infrastructure: 3
  science_code: 0
  science_exp: 0
timeline:
metrics:
  - "Toolkit and Interchange installable from a single package with unified versioning"
  - "All CI and tests pass without OpenEye installed"
  - "Toolkit wrapper abstraction layer removed; all cheminformatics calls go directly through RDKit"
go_no_go:
dependencies: []
enables: []
---

## Goals

- **Consolidate Toolkit and Interchange into a mono-repo** with unified versioning, CI, and release process — eliminating cross-repo synchronisation issues and making atomic changes across the parameterisation and system-export stack possible in a single PR. This may also include folding in smaller supporting packages such as openff-utilities, openff-units, and similar minor repos
- **Move to an RDKit-only cheminformatics backend**, removing the OpenEye toolkit wrapper abstraction layer and the associated testing/maintenance burden of supporting two backends
- *(Optional)* **Add a tensor representation** that enables direct translation from parameterised systems to smee tensors, bypassing the current Interchange object model

## Benefits

**Reduced maintenance burden.** The Toolkit and Interchange are tightly coupled but currently live in separate repositories, requiring coordinated releases, cross-repo CI, and careful version pinning. Merging them into a mono-repo eliminates this coordination overhead and makes refactoring across the parameterisation boundary straightforward.

**Simplified codebase.** The dual-backend cheminformatics abstraction (RDKit + OpenEye) is one of the most complex parts of the Toolkit. Every cheminformatics operation must be implemented and tested for both backends, and subtle behavioural differences between them are a recurring source of bugs. RDKit is now the dominant backend in practice — OpenEye usage has declined as RDKit's capabilities have improved and its PyPI availability has removed the last major installation barrier. Dropping the abstraction layer and going RDKit-only would significantly reduce code complexity and testing surface area.

**Unblocks external contributions.** The OpenEye backend requires a proprietary license key stored as a CI secret. Because GitHub Actions does not expose secrets to pull requests from forks, PRs from external contributors always fail the OpenEye tests. The only workaround would be granting public write access to the main repository so contributors can push branches directly — which is not acceptable from a security standpoint. This effectively blocks the open-source contribution model for any code that touches cheminformatics. Removing the OpenEye dependency eliminates this problem entirely.
