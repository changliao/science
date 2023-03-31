---
title: Issue in land river coupling in E3SM
date: '2023-03-31'
permalink: /posts/2023/03/31/land-river-coupling-issue
author: Chang Liao
tags:
- ESM
- Software
---

Recently when I was testing some land river coupling in E3SM, I found some longstanding issues. 

When the coupler needs to send fluxes or states from one to another, to conserve mass, the process sometimes needs to consider the area associated with it.

For example, if the flux is runoff, which is expressed as mm/day, then the coupler calculates the mass as: flux X area. However, within a grid cell, the area is partially covered by land, so area is calculated as: dArea_grid X dFraction_land. 

However, in the earlier development, this fraction of land is often set as 1.0 before lake and river are small at 1.0 degree resolution (~100km). This decision will make the area of river as 0.0.

The problem comes when we want to transfer flux from river back to land. 

Again, design decision in the earlier stage can cause problem in the later stage. Another example of technical debt. 