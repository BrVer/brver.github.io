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
1. check what data is required for an area to be visualized (for metropolitan areas we usually want to render multiple municipalities on a single map)
2. Parse ATOM/XML feed to get GML data archives URLs
3. Download/extract GML data (with caching).
4. Merge multiple data sources together.
5. Normalize geometry and CRS.
6. Extract construction year (different logic for different data sources).
7. Clip to desired 'center' coordinate + radius.
8. Bin years for visualization.
9. For each year in range - select buildings built by this year, plot and save output.
10. Combine outputs into a gif.

### AI involvement:
AI was able to:
- understand the entire required flow
- provide kinda-working-MVP script in Python (single data source into single picture)
- follow instructions to fix multiple encountered problems
- suggest how to write a similar script for the Basque Country / Navarra (they publish data in a different format), and gradually make it work.
- follow instructions to improve the scripts (e.g. combine multiple data sources, use caching etc.)
- follow instructions to combine pictures into gifs

### Results:

<img src="/assets/images/visualizing_urban_growth/valencia_growth_1960_2025_1y_step_4350m.gif" alt="Left image"/>

<img src="/assets/images/visualizing_urban_growth/madrid_growth_1960_2025_1y_step_12000m.gif" alt="Right image"/>

<img src="/assets/images/visualizing_urban_growth/barcelona_growth_1960_2025_1y_step_11500m.gif" alt="Left image"/>

<img src="/assets/images/visualizing_urban_growth/pamplona_growth_1960_2025_1y_step_5200m.gif" alt="Right image"/>

<img src="/assets/images/visualizing_urban_growth/bilbao_growth_1960_2025_1y_step_12000m.gif" alt="Left image"/>

<img src="/assets/images/visualizing_urban_growth/gijon_growth_1960_2025_1y_step_4000m.gif" alt="Right image"/>

[//]: # (<div style="display:flex; flex-wrap: wrap; margin-top: 16px">)

[//]: # (  <img src="/assets/images/visualizing_urban_growth/barcelona_growth_1960_2025_1y_step_11500m.gif" alt="Left image" style="width: 50%"/>)

[//]: # (  <img src="/assets/images/visualizing_urban_growth/madrid_growth_1960_2025_1y_step_12000m.gif" alt="Right image" style="width: 50%"/>)

[//]: # (</div>)

[//]: # (<div style="display:flex; flex-wrap: wrap;">)

[//]: # (  <img src="/assets/images/visualizing_urban_growth/valencia_growth_1960_2025_1y_step_4350m.gif" alt="Left image" style="width: 50%"/>)

[//]: # (  <img src="/assets/images/visualizing_urban_growth/pamplona_growth_1960_2025_1y_step_5200m.gif" alt="Right image" style="width: 50%"/>)

[//]: # (</div>)

[//]: # (<div style="display:flex; flex-wrap: wrap;">)

[//]: # (  <img src="/assets/images/visualizing_urban_growth/bilbao_growth_1960_2025_1y_step_12000m.gif" alt="Left image" style="width: 50%"/>)

[//]: # (  <img src="/assets/images/visualizing_urban_growth/gijon_growth_1960_2025_1y_step_4000m.gif" alt="Right image" style="width: 50%"/>)

[//]: # (</div>)

[//]: # (<p></p>)

[//]: # (![result]&#40;/assets/images/visualizing_urban_growth/results3x2.jpg&#41;)
[//]: # (<p></p>)
So far, I am quite excited about AI’s capabilities!