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



