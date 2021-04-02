---
title: 'Reducing the dependency of HexWatershed'
date: '2021-04-02'
author: Chang Liao
tags:
- HexWatershed
- GDAL
- NetCDF
---

When HexWatershed was developed in earlier days, I gradually added support for stream burning and a few other features.

The additions, in one way, make the model more powerful, and in another way, also introduce more dependency.

Now I am in the process of releasing a standalone Python package as a blinding for HexWatershed. The dependency becomes an issue because the binary cannot be built on-the-fly. 

One solution to this issue is to remove the features and move them into the Python package.

