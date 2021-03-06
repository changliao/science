---
 
title: 'Ecosystem modeling: model evaluation of current implementation in ECO3D 1.0'
date: '2017-04-05T20:02:00.001-07:00'
permalink: /posts/2017/04/05/eco3d_evaluation/
author: Chang Liao
tags:
- DOC
- MODFLOW
- TEM
- GIPL
- PRMS
modified_time: '2018-04-03T12:19:33.506-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-1180946385339429264
blogger_orig_url: https://changliao.blogspot.com/2017/04/ecosystem-modeling-006.html
---

As I am preparing my defense, the first version of ECOSYSTEM 1.0 in my thesis was finally completed. Looking forward to the next chapter of my life, I thought it is time to evaluate the ECOSYSTEM 1.0 to see what it is capable of and what still needs to be improved or expanded in the near future.

First, here is a brief introduction of the ECOSYSTEM model:
ECOSYSTEM is a three-dimensional water and carbon cycle terrestrial ecosystem model. Within ECOSYSTEM model, water and carbon cycle are seamlessly coupled. The water cycle is developed based on the PRMS, and the carbon cycle is developed based on TEM. The core idea behind the coupling is that both water and carbon (potentially nitrogen and others) fluxes can flow in a three-dimensional domain, and that is exactly one of the reasons why dissolved organic carbon (DOC) can be observed in stream water.

A lot of improvements have been made upon the original PRMS and TEM models. For example, I have added a new litter pool to consider the carbon pool, DOC leaching from the litter.

Even though model calibration of such kind of watershed hydrology-alike ecosystem model takes much effort, my initial model evaluation based on stream discharge, snow cover, GPP/NPP and DOC has shown that the three-dimensional approach have great potential. A good example could be something like the Riparian zone. I am also observing significant differences in soil moisture due to lateral water flow.

The ECOSYSTEM model is completely developed using C++11 with OpenMP enabled. A preview of the model structure was introduced in one of my early posts. One of the advantages of using C++ is that it's relatively easy to manage based on model structure, especially for models with sophisticated data I/O and flow.

Moreover, when I designed the ECOSYSTEM, a plugin approach/concept is used, which means that new processes can be easily added following the structure. This is also the same concept used in MODFLOW and PRMS.

With ECOSYSTEM, we can answer quite a few questions, including but not limited to:
How is surface hydrology responding to climate?
How is surface hydrology responding to land-use and land-cover change (e.g., wildfire)?
What is the role of lateral flow in soil moisture?
What is the role of lateral flow in carbon cycle?
What about DOC dynamics?
However, due to the time constrain, I haven't implemented some other important processes into the ECOSYSTEM model currently. And potentially I will keep working on this project and finish a newer version when time is right.

Here are a few processes that need to be added or improved in future development:
Groundwater flow is currently improved but not as good as MODFLOW, but it may be unnecessary to actually implement MODFLOW within ECOSYSTEM;
Soil water has different types of reservoirs, but the concept of layered model may improve vertical profile, which is also important for thermal process;
Soil thermal is currently simplified, it could be coupled with soil water using algorithm from TEM or other similar model such as GIPL;
Three-dimensional heat transport is missing, but with soil thermal (or even groundwater flow), it could be implemented;
Snow model currently does not consider heat from soil. A better layered snow model such as Snowpack can replace the current one;
A dynamical stream network may be added, which means the hydrology networks vary with  time;
Carbon and nitrogen coupling;
Thermokarst lake modeling is missing;
With thermal and soil carbon module, a new permafrost carbon release module could be implemented.
Hopefully, the last list will be shorted or even gone within one year.