---
 
title: Spatial variability of the SWAT model parameter
date: '2018-11-20T10:29:00.000-08:00'
permalink: /posts/2022/04/25/swat-parameter/
author: Chang Liao
tags:
- Model Calibration
- HRU
- Watershed Hydrology
- SWAT

---

How to consider the spatial variability of SWAT model parameter?
Should each HRU combination and each soil type has its own parameter set?

If so, then the total parameters number will be increased significantly. For example, if a SWAT model has 100 unique HRUs and we are interested in 5 HRU level parameter, then the total HRU associated parameter number is 500.

Some suggest to use a global ratio. In this case, there are also pros and cons:
Pros:

1. spatial variability can be preserved
2. total number can be reduced

Cons:

1. not strictly suitable for individual HRU
2. only works for some parameters. Paramter with negative value cannot be adjusted directly using ratio
