---
layout: page
title: "NetWeaver"
description: "Turn device inventories into proposed network segmentation plans."
importance: 3
category: "Network Tools & Engineering"
---

A device inventory tells you what is present, but leaves another question: how should those devices be organized? NetWeaver connects inventory data with proposed network boundaries for homes and small offices.

## From inventory to plan

Users paste or upload a CSV containing device hostnames, IP addresses, MAC addresses, and manufacturer information. The application classifies devices by network role, addressing needs, trust, and exposure, then develops a segmentation proposal.

## What it produces

- Device groupings across management, main, IoT, surveillance, guest, and unknown categories.
- Proposed VLAN assignments and subnet ranges.
- Addressing guidance and firewall allow/deny policy recommendations.
- Mermaid topology diagrams and network summaries.
- Exportable plan data in JSON or YAML.

The implementation includes rule-based classification, MAC-vendor lookup, and an optional model-assisted classification path. A React interface presents the analysis, with an Express backend and database storage for plans and inventories.

## Scope

NetWeaver works from supplied inventory data. Its classifications and exposure labels are planning judgments, not measurements of actual reachability. It generates recommendations rather than applying configurations to routers or switches.

The supplied code also uses the name **nmap.me** in parts of its interface and documentation.
