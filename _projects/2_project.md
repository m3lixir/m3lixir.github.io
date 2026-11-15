---
layout: page
title: "Chumdump"
description: "controlled bait and evidence records for defensive ai testing"
importance: 2
category: "security research & tooling"
---

When an AI system encounters a document, access alone does not establish what it did with the content. Chumdump provides a local workflow for placing traceable test artifacts and preserving the observations available in logs and telemetry.

## What it does

The CLI generates canaries, benign prompt-injection fixtures, retrieval bait, inert fake secrets, watermarks, lore seeds, and decoy documents. It packages them into bundles with manifests and index pages, then copies those bundles into a chosen local directory for deployment on an owned surface.

- Create and track controlled bait artifacts.
- Build website, retrieval-test, and agent-test bundles.
- Scan files for known bait and Chumdump markers.
- Correlate web access logs or JSONL telemetry with bait filenames, IDs, and canary tokens.
- Export Markdown, JSON, HTML, and SARIF-style evidence reports.
- Remove files recorded in a marked deployment.

## Interpreting the evidence

The evidence model distinguishes access, retrieval, repetition, instruction-following, leakage, and unclear behavior. The current implementation records these categories from supplied telemetry; it does not independently prove that a model obeyed an instruction or leaked information. Crawler labels are derived from user-agent strings.

`watch` processes a supplied log file once. Scanning detects recognizable markers rather than arbitrary malicious content.

## Scope

Chumdump is an early-alpha defensive testing tool for owned or authorized websites, documentation, retrieval corpora, and lab agents. The emphasis is on controlled experiments and inspectable evidence.

[View source](https://github.com/m3lixir/chumdump)
