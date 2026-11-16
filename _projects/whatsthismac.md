---
layout: page
title: "What's This MAC?"
description: "mac prefix vendor lookup with source context and address flags"
importance: 6
category: "network discovery & experimentation"
---

A MAC address can offer a useful clue about a device, but a vendor match is only one piece of evidence. What's This MAC? makes prefix lookup accessible while exposing information that helps users judge the result.

## Lookup and context

The application normalizes full or partial MAC addresses and searches its vendor database for the most specific available prefix. Its lookup logic supports 24-, 28-, and 36-bit assignments.

Results include the matched vendor, prefix length, assignment type, source, confidence indicator, and conflict flag. The API also flags locally administered and multicast addresses.

## Interfaces

- Web interface for looking up address prefixes.
- Single and batch lookup API endpoints.
- Vendor and data-source endpoints.
- Downloadable prefix data in CSV and JSON.

The implementation uses a React frontend, an Express API, and PostgreSQL storage through Drizzle.

## Scope

Prefix assignments indicate registry or database associations; they do not establish a device's exact model, owner, or trustworthiness. Confidence indicators follow source and conflict rules rather than representing a measured probability of device identity. Locally administered addresses need particular care when interpreting vendor matches.
