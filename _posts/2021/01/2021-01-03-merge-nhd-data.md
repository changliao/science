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

In the shapefile attribute table, we can add two fields to define the stream segment information.
* Stream order
* Stream segment index

Ideally, we can break the whole line feature into parts then re-build the topology.

The follow steps may work:
1. Remove erros in line feature, mainly loops
  * loop

    ![Figure 1](https://github.com/changliao/science/blob/main/_figure/hexwatershed/flowline_loop.png?raw=true)

  * short path

    ![Figure 2](https://github.com/changliao/science/blob/main/_figure/hexwatershed/short_path.png?raw=true)
2. Merge all flowline together
3. Merge features into one single feature
4. Break into parts

  * [Feature to line](https://desktop.arcgis.com/en/arcmap/10.3/tools/data-management-toolbox/feature-to-line.htm)
  
5. Define outlet (this step might need DEM)
6. Define segment
7. Define order
8. Write into a new shapefile

We might be able to add other attributes later if needed.

If possbile, we can implement all the steps within Python without using ArcGIS API.
However, step 1 requires manual examination, so we can try ArcGIS first. Then the following steps can be carried out using Python.

