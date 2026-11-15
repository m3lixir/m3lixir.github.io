---
layout: page
title: "LAN Browser"
description: "a mobile browser for local device interfaces and development servers"
importance: 5
category: "network discovery & experimentation"
---

Routers, appliances, and development servers often expose their controls through a local web page. LAN Browser provides a focused mobile interface for opening those pages by IP address or URL.

## What it does

- Accepts a manually entered address and adds an HTTP scheme when needed.
- Provides shortcuts to common local addresses.
- Keeps a short recent-address history during the session.
- Offers back, reload, loading, and retry controls around an embedded WebView.

The application is built with Expo, React Native, and React Native WebView.

## Scope

LAN Browser opens addresses supplied by the user or selected from shortcuts. It does not scan the network, discover services, or identify devices. Access depends on the local service, network connectivity, and the platform's web-view behavior.
