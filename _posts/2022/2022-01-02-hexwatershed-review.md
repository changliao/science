---
 
title: A review of HexWatershed and its future application
date: '2022-01-02'
permalink: /posts/2022/01/02/hexwatershed-review
author: Chang Liao
tags:
- Hydrology
---

Almost 4 years ago, I decided to write a model that can be used for the 3D land surface model routing component. At that time, they were already plenty of global routing models, except that all of them are for coarse spatial resolution. I need to create a model that is for high spatial resolution. However, this is an impossible task back then because I cannot run existing tools/models directly. The reason is that (1) existing regional scale model cannot be run at global scale; (2) global scale data usually has a different spatial reference. All of these lead me to develope the unstructured mesh-based flow direction model.

I started with DGGrid, which is exactly what we need for global scale hydrology. It provide uniform resolution, so spatial reference issue can be resolved. It is generally considered well designed and structured, so it would be easy to implement existing method on top of the mesh.

Dealing with a new mesh means we need new algorithm to define neighbors, or the index system. I spent some time comparing different index system for unstructured meshes. 

Other than that, I need to implement a depression filling using the new mesh. By the time I wrote ECO3D, I already have some experience in the terrain analysis based on the USGS CRT model. 

It was not easy to sell a new idea even though it seems attractive at the first sight. We all admit it would be useful to improve the hydrologic model, but how much improvements? how much efforts are needed to prove it? We don't have much idea at the time. Especially that we already some well developed and established traditional tools. But I know without this, we can never resolve the issue that high latitude can be fairly represented in Earth system model.

I wrote a small proposal to test my idea and fortunately I got just enough funding to support it. Because time is limited, I started at a regional scale because it is much more complicated at a global scale. The HexWatershed 1.0 was born after one year. It is a rather simple model without many features. However, our analysis show that it does make lots of differences compared with the traditional method. This gave us some confidence that it may actually work for global hydrology. But we need funding for the next step.

Later on, DOE's ICoM project was funded. In ICoM, it was the first time that a unified mesh was proposed to connect land, river, and ocean in Earth system model. To do so, the river component needs a new routing map using the unstructured mesh, the MPAS mesh. Interestingly, the MPAS mesh is just the DGGrid mesh, except that it is variable resolution. Therefore, I joined the ICoM team to further improve the HexWatershed model to support the MPAS mesh.

A lots of things or features were also requested during the development. Such as that stream burning is needed because we want the flow direction is accurate at any resolution. We also add feature to consider dam in the workflow so dam management aligns with river network. To run the model at a global scale, we also change the way to consider boundaries. One unique feature we invented is the topology-based stream burning, which we will introduce in our next paper. Other features are also gradually added, such as in-land lakes.

Looking back, lots of assumptions and applications have changed. For example, at the beginning, I was not considering the ocean. With lots of discussion within our team at PNNL and LANL, we are now entering some exciting and yet challenging territories. For example, we gradually realized that the boundary between regional scale hydrology and global scale hydrology is disappearing because our variable resolution ranges between 50km and 2km. Also, our domain changes with time: a region of interest may be partially land and partially ocean in different time steps.

There are still lots of aspects we haven't touched, such as the Arctic, which is where our new mesh would be even more useful. But we are paving the pathway to get there soon.

Through the development, I personally learned a lot of both science and technology practices. 
I also strive to share our study with the boarder hydrology community. I will release both the HexWatershed model and its byproduct PyFlowline as Python packages so hydrologic models can try them out in their own research. Look forward to 2022 to make this happen.

