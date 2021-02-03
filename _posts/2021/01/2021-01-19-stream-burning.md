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

Can we ignore short flowline?
![Figure 4](https://github.com/changliao/science/blob/main/_figure/hexwatershed/algorithm/flowline4.png?raw=true)
If they are removed, do we need to merge the remaining two segments as one?

We cannot create discontinuity after simplification.


How about this one?
![Figure 5](https://github.com/changliao/science/blob/main/_figure/hexwatershed/algorithm/flowline5.png?raw=true)


An upgraded version of stream burning is able to resolve some issues.

![Figure 6](https://github.com/changliao/science/blob/main/_figure/hexwatershed/algorithm/flowline6.png?raw=true)

* First, the zig-zag pattern in red rectangle shows the topology information can be preserved on main channel
* Second, the yellow rectangle shows that threshold is important if we don't have topology in low order streams

Ultimately, if the stream flowline topology can be simplified and burned into mesh, the fully breaching-filling approach will be possible although it is not an easy task. If not, auto breaching on main channel and full breaching on low order streams seem to be able to keep flow direction mostly correct but modification to DEM wil be substantial. 

If full topology is available, when a grid searches for upslope, it must loop through by stream order, then to land. It will won't resolve issue illustrated in the green rectangle easily (We may break some flowline features again).

Overall, it is likely we should generate topology before actual filling, which may simplify some processes significantly.
