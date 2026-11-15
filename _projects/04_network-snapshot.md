---
layout: page
title: "Network Snapshot"
description: "Connection details and basic LAN discovery in a mobile dashboard."
importance: 4
category: "Network Tools & Engineering"
---

Network troubleshooting often starts with a few basic questions: what network is this device using, what is its public address, and which local interfaces respond? Network Snapshot brings those observations into one mobile dashboard.

## What it shows

- Public IP address from an external IP lookup service.
- Local IP, connection type, and connectivity state.
- Wi-Fi network name when permissions and platform support allow it.
- Local addresses responding to HTTP probes on selected ports.
- A downloadable or shareable text report.

## How discovery works

The Expo and React Native implementation derives a candidate `/24` address range from the device's IPv4 address. It sends HTTP HEAD requests to selected ports in batches and displays responding addresses with the port observed.

## Scope

This is basic HTTP-based discovery rather than comprehensive network enumeration. Devices without responding HTTP services may be missed, and platform networking restrictions affect results. The candidate range assumes a `/24` network; it is not derived from the actual subnet mask. Header-derived labels should not be treated as verified hostnames.
