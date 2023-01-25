---
title: Mesh independent vs Topological relationship
date: '2023-01-23'
permalink: /posts/2023/01/23/mesh-independent-or-topological-relationship
author: Chang Liao
tags:
- HexWatershed
- PyFlowline
---

`PyFlowline` is mesh independent, and it uses topological relationship to model river networks. But what are the relationships between these two features? This is also the question I asked myself when presenting the model to the team members.

For example, one may ask "Which feature is more important?" or "Can I turn off the topological relationship feature?"

To understand their relationships, we also need to consider HexWatershed.

From one side, without topological relationship, river networks become a binary mask. And that means we cannot produce conceptual river network using PyFlowline anymore. However, HexWatershed is still able to produce it after watershed delineation. From this perspective, topological relationship must be on for PyFlowline, but not for HexWatershed.

Then what makes the model `mesh independent`? Both models were designed in a way that it does not rely on 2D index. 


