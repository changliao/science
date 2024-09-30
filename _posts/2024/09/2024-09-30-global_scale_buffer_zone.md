---
title: How to calculate the buffer zone on the global scale
date: '2024-09-30'
permalink: /posts/2024/09/30/global-scale-buffer-zone
author: Chang Liao
tags:
- ESM
- Software
- GDAL
---

It is relatively simple to calulate the buffer zone at the regional scale because we can use a map projection. However, if we need to calculate the buffer zone at the global scale, there isn't a way so far. 

The real challeage is that at the global scale, we cannot use a single map projection. In order for an algorithm to work on the global scale, it must accept either (1) latitude-longitude based system, or (2) 3D x-y-z coordinate system.
Currently, there isn't a model or tool that accept either of them. 

To resolve this issue, I built a customized GDAL from the source code and this model uses the latitude-longitude based system to calculate the proximity distance. 
To run the tool, the following steps are needed:

* Clone the git repository from: git@github.com:changliao1025/gdal.git
* Check out the changliao branch using VS Code or Git command git checkout changliao
* Create a Python environment using conda
    If you are on a HPC, you first need to load the correct module such as: module load conda/Miniconda3-py311_23.11.0-2.lua
    You also need to load the cmake: module load cmake/3.24.3
    Then you can create a conda environment using:
    “conda create –name gdal cxx-compiler gcc python zlib libarchive shapelib proj expat xerces-c numpy swig netcdf4 libpng ” 
    This environment will meet most of the requirement for the build, but if you receive any error in later steps, you may need to add additional python packages during this step. 
* Activate this conda environment using conda activate gdal
* Set up cmake configuration using the conda environment. This is critical because many gdal API will not work for system wide compilers
    export CC=~/.conda/envs/gdal/bin/gcc
    export CXX=~/.conda/envs/gdal/bin/g++
    export CMAKE_PREFIX_PATH=~/.conda/envs/gdal
    export LD_LIBRARY_PATH=~/.conda/envs/gdal/lib:$LD_LIBRARY_PATH
* Build the gdal following the instruction from: https://gdal.org/development/building_from_source.html
* Change directory to the download git repository
* mkdir build
* cd build
* cmake -DCMAKE_INSTALL_PREFIX=~/.conda/envs/gdal -DGDAL_PYTHON_INSTALL_PREFIX=~/.conda/envs/gdal  -DBUILD_JAVA_BINDINGS:BOOL=OFF -DBUILD_SHARED_LIBS=ON -DBUILD_CSHARP_BINDINGS:BOOL=OFF .. > out.txt 2>&1
* cmake --build .
* cmake --build . --target install
* Once you see this line:
    -- Installing: /global/homes/l/liao313/.conda/envs/gdal/lib/pkgconfig/gdal.pc
    That means you have successfully built gdal within a conda environment, and you can call gdal python API as usual. 

This still does not fully solve the problem because the left and right edges are not connected. 
