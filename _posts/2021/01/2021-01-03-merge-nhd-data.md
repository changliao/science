---
title: 'Merge hydrography from different sources'
date: 2020-10-12
permalink: /posts/2021/01/03/merge-nhd-data/
excerpt: Merge hydrography data from different sources using Python and GDAL.
author: Chang Liao
tags:
  - Watershed
  - Hydrology
  - Vector
---

Sometimes the NHD datasets are not complete if the study area across bounders.
In this post I will show you how we can merge different datasets into a predefined format for hydrology research.

When we merge stream networks data from different sources, the first question is what do we need to generate in the final product.
* Stream segment 
* Stream order
* Stream confluence

And what format we want the data to be stored?
* Shapefile
* NetCDF

Considering that the current NHD is using Shapefile and the hexagon mesh is also shapefile, one direction we can take is shapefile.

GDAL supports API level intersection, so it is also possible to use another format.
[GDAL Geometry](https://gdal.org/python/osgeo.ogr.Geometry-class.html)

This process can be coded into the Python package as well.

As a start, we can rely on Shapefile for testing purpose.


