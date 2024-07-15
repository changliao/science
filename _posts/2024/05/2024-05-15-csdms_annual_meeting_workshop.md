---
title: Mesh-independent flow direction modeling using HexWatershed 3.0
date: '2023-03-02'
permalink: /posts/2024/05/15/mesh-independent-flow-direction-modeling-using-hexWatershed-3
author: Chang Liao
tags:
- ESM
- Software
- HexWatershed
- Workshop
---

After attending the CSDMS annual meeting in 2022, I have continued collaborating with the CSDMS community. Special thanks to all the people who provided feedback on our HexWatershed model.
This year, the annual meeting organization contacted me again to ask whether I would be interested in attending the meeting and giving another tutorial. 
Lots of progress has been made over the past two years, coming from both DOE's ICoM and InteRFACE projects. HexWatershed also received lots of updates and improvements, including the model structure and I/O/ 
So I said yes and started to organize the new materials based on our recent work. 

In this year's tutorial, after several round of discussion with the team, I adopted a new workflow to break the barrier between us as model developers and users. That is the web browser-based jupyter notebook. 
https://github.com/changliao1025/hexwatershed_tutorial

There are several significant designs in this workflow:
* use mybinder (https://mybinder.org/) to host the entire environment, so users don't need to install anything to run all code
* separate Python and C++ code: this is not an ideal solution, but it works best currently for me as a developer to isolate different environments
* Adopt the latest Python package structure in PyEarth, PyFlowline, and HexWatershed; each package is maintained in a different Python package, making it much easier for CI/CD.

Besides, in this workshop, I used a different mesh type, the DGGRID mesh, which is very popular in the GIS DGGS field but not well recognized in the geophysics field. 

My collaborator Matthew G Cooper provided lot of help in this workshop as he helped with the testing and design, especially from a user's perspetive. For example, we changed the model configuration module. I also developed a new model input checking machnism inspired by his confusion about the model domain boundary input. (remember the linux bash profile/bashrc nightmare?)

We had a relatively minor group of attendees but still received lots of questions and suggestions, which are gradually integrated back into our model right now. 
