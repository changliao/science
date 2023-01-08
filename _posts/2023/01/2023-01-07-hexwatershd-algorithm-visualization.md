---
title: Visualization of the priority flood algorithm within HexWatershed
date: '2023-01-07'
permalink: /posts/2022/07/08/visualization-priority-flood
author: Chang Liao
tags:
- Visualization
- HexWatershed
- Depression filling
- Priority flood
---

HexWatershed uses several algorithms to generate most flow routing parameters, including the depression-free elevation. 

However, because of the incorporation of stream burning, the original priority flood algorithm has been upgraded to include the classical DEM reconditioning algorithm. 
The mix of two distinct algorithms under the same umbrella leads to a level of complexity, for both the developer and the end user. A few additional features make this workflow even more complex:

* It is designed to support structured and unstructured meshes
* It is designed to support regional and global scale simulations

A visualization of the algorithms is essential to diagnose and understand the model. 

In the early stage of HexWatershed development, I was also inspired by [RedBlogGames by Amit](https://www.redblobgames.com/grids/hexagons/). 

The interactive visualization is helpful for some algorithm design and implementation. Since I am not familiar with those web-based interactive visualization, I decided to use Python as a start.

In this post, I provide a visualization of the stream-burning built-in priority flood algorithm using a case study.

First, below is animation of how HexWatershed processes the elevation of each MPAS cell. 

![Figure 1](https://github.com/changliao/science/blob/main/_figure/hexwatershed/algorithm/priority_flood.gif?raw=true)

This animation is not meant to demonstrate the results of depression-filling, but instead focuses on how the algorithm processes the domain cell by cell. In general, there are two major steps:

1. The algorithm starts at the boundary, find the river outlet, then search upstream using a binary search method. There are also two sub-steps in this step:
    * The algorithm processes river first, then its upstream.
    * The algorithm process river first, then its riparian zone.

2. The algorithm then pushes the whole domain boundary, and conduct the classical priority-flood depression filling. It will automatically skip river cells which are already processed.

Although the animation suggests that each cell is processed only once. In reality, river cell may be processed multiple times due to the breaching method.

Besides, two texts are placed at the active cell left and right. If the right side is higher, the elevation is increased. Or else, it is decreased.

At the end of the animation, you will notice there are several holes, or islands. They are peaks/summit. The algorithm will still perform although the domain is broken into several parts.

Next, below is zoom-in view following the algorithm.

![Figure 2](https://github.com/changliao/science/blob/main/_figure/hexwatershed/algorithm/priority_flood_track.gif?raw=true)

Email me if you have any questions.



