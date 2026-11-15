---
layout: page
title: "TDFF"
description: "Taint-guided input mutation for embedded firmware research."
importance: 1
category: "Security Research & Tooling"
---

Embedded firmware depends on hardware interactions that make conventional software testing difficult. TDFF explores whether dynamic taint analysis can help choose more useful inputs when each execution is expensive.

## Approach

The prototype follows a record, replay, and explore loop. Avatar2 coordinates execution with the embedded target; PANDA replays recorded execution for analysis. Tainted branch information identifies input bytes that influence conditional branches, guiding deterministic mutations rather than changing every byte indiscriminately.

The custom `io_taint` PANDA plugin is part of this project. It labels reads in a configured memory-mapped I/O range and logs executed basic blocks. The Python driver uses the resulting logs to guide input mutation and track newly observed blocks.

## Implementation

- Hardware-assisted recording and PANDA replay for embedded firmware analysis.
- Input mutations using bit flips, small arithmetic changes, and selected byte values.
- Device-specific configuration and recording scripts.
- Examples targeting Nucleo boards, including a firmware port of Libtasn1.

## Findings and limits

The 2020 master's thesis demonstrated the approach on a small branch-reaching example. The more complex example was not solved, and the Libtasn1 evaluation did not reproduce known vulnerabilities within the reported run. Serial input overhead and emulation constraints limited scalability.

TDFF is a research prototype: its contribution is the implementation and evaluation of a taint-guided workflow for embedded systems, including the limitations encountered.

## Research and code

- [Read the thesis]({{ '/assets/pdf/savich2020taint.pdf' | relative_url }})
- [TDFF source](https://github.com/m3lixir-nyu/tdff)
- [I/O taint plugin](https://github.com/m3lixir-nyu/io_taint)
