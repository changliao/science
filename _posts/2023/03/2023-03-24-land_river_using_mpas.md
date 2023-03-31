---
title: How to couple land and river model using a MPAS mesh
date: '2023-03-24'
permalink: /posts/2023/03/24/land-river-coupling-using-mpas-mesh
author: Chang Liao
tags:
- ESM
- Software
---

The E3SM river component MOSART can be run using a MPAS mesh. However, the MOSART requires forcing data such as surface runoff from a land model.

If the land model is not turned on, we can still run the MOSART with external forcing data, which is often not using the MPAS mesh. 

This article explain how to run a coupled lnd-rof-(atm) simulation with the rof on the MPAS mesh. 

We need to carry out several steps, but not necessarily in the following order:

* Generate the MPAS mesh-based MOSART parameters, and generate the domain file;
* Generate the envolope lnd domain using the MOSART domain file, use this domain file as the atmosphere domain as well (somehow datm is still needed for some bad reason)
* Generate the mapping between these two domain files
* Since now land and river are not on the same grid, we need to create a new compset/grid to reflect this
* Update the coupler so the dlnd variable can be accepted. In general, the dlnd will use the mapping file convert stream files, then they are passed to coupler through l2x
* Update the coupler so the rof can accept the incoming variable through x2r



