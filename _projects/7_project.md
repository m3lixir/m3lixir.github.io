---
layout: page
title: "Crop to Content"
description: "Trim empty image borders with adjustable thresholds and background controls."
importance: 7
category: "Applications & Automation"
---

Removing empty space around an image should not require adjusting four crop handles by hand. Inspired by GIMP's Crop to Content, Crop to Content automates that repetitive step through a mobile interface.

## What it does

The image processor finds a content bounding box using transparency or an estimated uniform edge color, then crops the original image to that region.

- Simple trimming with preset color tolerance.
- Advanced controls for color tolerance and transparency thresholds.
- Color-based background removal.
- Background replacement with a color, pattern, or supplied image.
- PNG output and a history interface.

## Implementation

An Expo and React Native client sends images to an Express backend. Sharp performs pixel analysis, cropping, and compositing. Larger images are analyzed at reduced resolution before the crop is applied to the original image.

## Scope

The current implementation uses pixel-based heuristics. AI segmentation is a planned feature, and processing currently runs on the server rather than entirely on the device. Complex backgrounds, shadows, and foreground colors similar to the background can affect the result.
