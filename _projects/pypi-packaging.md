---
id: pypi-packaging
title: "PyPI packaging"
category: usability
recommended: true
stages:
  - infra_updates
summary: "Move core OpenFF packages to PyPI with optional AmberTools dependency, drastically lowering the barrier to installation for new users and enabling use in pip-only environments."
fte:
  infrastructure: 0.5
  science_code: 0
  science_exp: 0
timeline:
  - milestone: "openff-toolkit and openff-interchange available on PyPI"
    date: "Q3 2026"
metrics:
  - "pip install openff-toolkit works without conda for all core use cases (parameterisation, system building, export)"
  - "AmberTools made optional; core functionality available without it"
  - "CI green on pip-only environments (Linux, macOS, Windows) with modern Pythons"
  - "Installation instructions in all tutorials updated to offer pip as the default path"
  - "Number of unique monthly PyPI downloads tracked as adoption signal post-release"
go_no_go:
  - gate: "Q3 2026"
    condition: "All hard conda-only dependencies either resolved or confirmed scopeable to optional features; if a core dependency cannot be PyPI-published within the timeline, reassess scope to a partial release"
dependencies: []
enables: []
---

## Goals

- Make AmberTools an optional dependency invoked only when AMBER-format output or AM1-BCC charges are requested, not required for basic force field loading and parameterisation
- Publish openff-toolkit and openff-interchange (and any key supporting packages) to PyPI with appropriate version pinning
- Update all documentation, tutorials, and workshop materials to list pip as the primary installation method

## Benefits

Currently, OpenFF packages are only available via conda, which creates a significant barrier for the large population of Python users who work exclusively in pip environments. This includes data scientists using Google Colab or JupyterHub, developers building Docker images or CI workflows, and users in corporate environments where conda is not available or is prohibited by IT policy.

PyPI availability dramatically expands OpenFF's accessible user base, enables installation in cloud and container environments without special setup, removes the conda requirement from tutorials and workshops (reducing friction for new learners), and aligns OpenFF with the standard Python packaging ecosystem. Several industrial users have specifically cited the conda-only requirement as a barrier to broader internal adoption.

RDKit — historically a major conda-only dependency — is now available on PyPI for Linux, macOS, and Windows, removing what was previously the largest blocker.
