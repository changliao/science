---
 
title: Calculating the area in a 3D space
date: '2022-01-02'
permalink: /posts/2022/01/02/pyflowline-area-of-diff
author: Chang Liao
tags:
- Hydrology
---

In the HexWatershed model, we invented a new metric to evaluate the closeness of the modeled river network with real ones. This concept involves the calculation of ares from two sets of vector-based flowlines. The calculation, however, is not trival.

Normally, we calculate area in a 2D space, such as on a screen or after the projection. In a 3D space, the concept or definition needs to be adjusted. If the vertices of a closed geometry are not on the same plane, we cannot calculate the area without projection.

In Earth science, this projection plane can be the Earth surface, which itself is a sphere. In this case, we can calculate the area of a polygon consists of multiple lat/lon points.

Besides, in a 3D space, the left and right concept is different. As a result, if a point is connected to three line segments, which one is most right one to the other one is not easy to define. This requires an updated angle formula on the sphere.



