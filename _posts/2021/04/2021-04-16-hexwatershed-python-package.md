---
title: 'HexWatershed Python package'
date: '2021-04-16'
author: Chang Liao
tags:
- HexWatershed
- GDAL
- NetCDF
- Python
---

After recent discussion, it is clear that a Python package should be developed to make HexWatershed available to boarder audience.
This decision means that there is much ongoing effort to re-structure the data flow and related algorithms behind HexWatershed. Below I will introduce some steps/efforts we made or will make in the next phrase of development.

# Data flow design

The core idea behind the Python package release is to remove the dependency of HexWatershed on GDAL and NetCDF C++ APIs.
With Python, this is much easier because Python has robust support for them already. 

1. One option we considered is pure Python rewrite using Numba
https://numba.pydata.org/
2. We also consider cython to provide interface to C++ library.
https://cython.org/
3. The last option we consider is to use cmake within Python setup script.
https://pypi.org/project/cmake/

Each of these options have different pros and cons. 
Computational cost is a factor we consider because HexWatershed is designed to be run at global scale with high resolution.
A coarse resolution (60km resolution) simulation was done earlier. Using the default configuration on a typical HPC, the runtime core hour is approximately 1hr.

A safe move we take at this moment is to keep C++ core algorithms, so we picked the third option for now.
While option 2 and 3 can be similar if we blend dynamics library with actual executable.

The difference between 2 and 3 means that whether a data format has to be used to transfer data.
In option 2, we may transfer directly using data structure, which may be complex and required careful design.
In option 3, we can write data into a intermediate file format and let the HexWatershed C++ program read the data.

In either way, having a data format may provide us some skills to analysis.

# Data format

A data format means what type of API we have to use in order to process data.
Most hydrography data use both raster and vector to store flowline, elevation, etc. 
We do not want to introduce dependency because of data format. For example, we want the HexWatershed can read all the information without additional libraries. This was not the case in version 2 because of Shapefile and NetCDF. Now with Python, we can get rid of them both.

A text based format will be ideal because it can be read and written easily without additional APIs. However, organization of information using pure text is also not easy. Therefore, we decided to use JSON and GeoJSON to store all the data. it is text based, and it can be processed by both Python and C++ (a few header files).

One advantage of JSON is that it has not file size limit as that of Shapefile.

# Python package setup

To set up the package, I just followed some common steps, which are similar to those explained here;
https://packaging.python.org/tutorials/packaging-projects/

Because HexWatershed has C++ component, I used the dynamics way to setup. Currently, I have not configured the cmake part because the C++ part is still under development.

# Python package index 

Next, we can add the package to PyPI.
https://packaging.python.org/tutorials/packaging-projects/

# Github action setup
Once a package is deployed, I started to fix some existing bug and improve code quality.
This can be done using Github action for perform CI/CD.

https://packaging.python.org/guides/publishing-package-distribution-releases-using-github-actions-ci-cd-workflows/

One way I prefer is first update one, then create a dedicated token for this repo.
Using release from Github to reduce unnecessary update to PyPI seems to work fine to me.

I was not very comfortable with the https://semver.org/ method at the beginning. But it seems to be very helpful in the long run. Because I want to make the package less dependent, the version number is actually easy to control.


