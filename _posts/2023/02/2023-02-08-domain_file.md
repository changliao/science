---
title: The domain file in ESM
date: '2023-02-08'
permalink: /posts/2023/02/08/the-domain-file
author: Chang Liao
tags:
- ESM
- Software
---

In order to set up a MPAS mesh-based MOSART/ELM simulation, I need to prepare a ``domain file``.

After some effort, I was not able to find any documentation describing the so-called domain file.

However, I found quite some documentation on how to generate this domain file, such as: https://www2.cesm.ucar.edu/models/cesm1.2/clm/models/lnd/clm/doc/UsersGuide/x11812.html

Without looking at the official documentation, the only way to understand the structure of the domain file is through existing files and possibly code.

In general, the domain file stores the information of mesh cells, including cell center, vertices, and area.

The cell center is either a 1D (unstructured) or 2D (structured) array.

As a result, the vertices can be a 2D or 3D (structured) array. In practice, the vertices array often uses the (nj, ni, nv) structures to store the data.

For unstructured mesh, we can set `nj` or `ni` as 1.
