---
title: 'Stream burning across resolution'
date: 2021-01-19
permalink: /posts/2021/01/19/stream-burning/
excerpt: Stream burning across resolution
author: Chang Liao
tags:
  - Watershed
  - Hydrology
  - Vector
---

Can we teach the algorithm as smart as human?



![Figure 1](https://github.com/changliao/science/blob/main/_figure/hexwatershed/algorithm/flowline1.png?raw=true)



![Figure 2](https://github.com/changliao/science/blob/main/_figure/hexwatershed/algorithm/flowline2.png?raw=true)


  
![Figure 3](https://github.com/changliao/science/blob/main/_figure/hexwatershed/algorithm/flowline3.png?raw=true)

Some un-confirmed workflow:

* Start from outlet, reversely searching
* Identify confluence A
* Search neighbors of A
* Check whether there is confluence in neighbors
* Identify non-confluence neighbors

when a grid has multiple segment, how to define priority?
* high stream order first
* confluence first
* Longest path possible (using edge vertex)


