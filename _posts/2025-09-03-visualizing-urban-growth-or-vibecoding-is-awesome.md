---
layout: single
title:  "Vibecoding spanish cities construction year maps"
date:   2025-09-03 10:55:24 +0200
tags: vibecoding visualisation plotting
excerpt: 'Checking what AI is capable of nowadays'
---

Inspired by [https://dominicroye.github.io/blog/visualize-urban-growth/](https://dominicroye.github.io/blog/visualize-urban-growth/), 
I decided to visualise and compare various spanish cities maps (and also check how good AI is at doing this job)..

### Pipeline:
1. check what data is required for an area to be visualized (for metropolian areas we usually want to render multiple municipalities on a single map)
2. Parse ATOM/XML feed to get GML data archives URLs
3. Download/extract GML data (with caching).
4. Merge multiple data sources together.
5. Normalize geometry and CRS.
6. Extract construction year (different logic for different data sources).
7. Clip to desired 'center' coordinate + radius.
8. Bin years for visualization.
9. Plot and save output.

### AI involvement:
AI was able to:
- understand the entire required flow
- provide kinda-working-MVP script in Python
- follow instructions to fix multiple encountered problems
- suggest how to write a similar script for the Basque Country / Navarra (they publish data in a different format), and gradually make it work.
- follow instructions to improve the scripts (e.g. combine multiple data sources, use caching etc.)

### Results:
![result](/assets/images/spanish_cities_results.jpg)

![gif](/assets/images/valencia_growth_1940_2025_5y_step_4350m.gif)

So far, I am quite excited about AI’s capabilities!