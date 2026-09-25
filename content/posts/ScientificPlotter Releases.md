---
date:  '2026-07-22T22:00:01+09:00'
lastmod: '2026-09-26T00:27:28+09:00'
draft: false
title: 'ScientificPlotter Releases'
tags: ["ScientificPlotter","macOS","Scientific Visualization"]
author: ["Yuchen Gu"]
math: False
---

ScientificPlotter is a native macOS application for scientific data visualization.

I started this project because I wanted a plotting tool that feels at home on macOS while still providing the features needed for research and numerical work. The goal is not to replace every established plotting package, but to offer a focused and responsive desktop application for exploring data, preparing figures, and exporting publication-ready graphics.

Main features include:

- XY line, scatter, and analytical function plotting
- 2D contours and interactive 3D surfaces
- 2D and 3D finite-element visualization
- Data import and reusable analysis workflows
- 3D scene composition and 2D diagrams
- Multi-panel figures with custom layouts, legends, and zoom insets
- PNG, vector PDF, and scientific data export
- Versioned `.splot` projects with checkpoints
- Stable and invite-protected Beta update channels

ScientificPlotter 2.0.0 requires an Apple Silicon Mac running macOS 27 or later. This release has been qualified on an M4 Pro Mac.

The app is distributed through GitHub with ad-hoc signing, without Apple Developer ID signing or notarization. On first launch, macOS may require **Open Anyway** under **System Settings → Privacy & Security**.

---

## Version 2.0.0 — September 26, 2026

This release adds:

- Data analysis and analytical function plotting
- 2D and 3D finite-element visualization
- Model and Scene workspaces, including 3D composition and 2D diagrams
- Custom legends, zoom insets, and flexible figure layouts
- Expanded colormaps and unified export tools
- Project checkpoints and workflow improvements

…and more.

Back up existing `.splot` projects and linked FEM files before upgrading. Projects saved in 2.0 may not open in older versions; use **Save As** to preserve the originals.

[Download ScientificPlotter 2.0.0](https://github.com/ycgu/ScientificPlotter-Releases/releases/tag/v2.0.0)

---

## Version 1.1.0 — July 22, 2026

Version 1.1.0 is the first release that I feel comfortable sharing for regular use.

This update focuses on stability and interaction quality. Plot navigation, plot switching, project saving, and multi-window handling are now more reliable. XY plots, 2D contours, scatter plots, and the 3D contour renderer have also received substantial visual and performance improvements.

The release also introduces independent Stable and Beta update channels with signed and verified update packages.

There is still more to improve, but ScientificPlotter now has a solid foundation for exploring numerical data and preparing scientific figures.

[Download ScientificPlotter 1.1.0](https://github.com/ycgu/ScientificPlotter-Releases/releases/tag/v1.1.0)

[View all releases](https://github.com/ycgu/ScientificPlotter-Releases/releases)

---

<!--
Append future releases below using this structure:

## Version X.Y.Z — Month DD, YYYY

A short introduction to the release.

### Highlights

- Change one
- Change two
- Change three

[Download ScientificPlotter X.Y.Z](https://github.com/ycgu/ScientificPlotter-Releases/releases/tag/vX.Y.Z)
-->