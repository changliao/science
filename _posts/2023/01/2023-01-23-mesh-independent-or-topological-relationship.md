---
title: Mesh independent vs Topological relationship
date: '2023-01-23'
permalink: /posts/2023/01/23/mesh-independent-or-topological-relationship
author: Chang Liao
tags:
- HexWatershed
- PyFlowline
---

`PyFlowline` is mesh independent, and it uses `topological relationship` to model river networks. But what are the relationships between these two features? This is also the question I asked myself when presenting the model to the team members.

For example, one may ask "Which feature is more important?" or "Can I turn off the topological relationship feature?"

To understand their relationships, we also need to consider HexWatershed.

From one side, without topological relationship, river networks become a binary mask. And that means we cannot produce conceptual river network using PyFlowline anymore. However, HexWatershed is still able to produce it after watershed delineation. From this perspective, topological relationship must be on for PyFlowline, but not for HexWatershed.

Then what makes the model `mesh independent`? Both models were designed in a way that it does not rely on 2D index, which also means some traditional methods can be extended to mesh independent if the 2D index structure assumption can be abandoned.

| Feature      | What if without | Relation|
| ----------- | ----------- |----------- |
| Mesh independent      | Cannot couple river and other hydrologic features  |  Does not concern topological relationship, but it helps capture details |
| Topological relationship   | Cannot assist stream burning  |  Supports unstructured mesh by default |

For PyFlowline alone, topological relationship may be more important because it is how the model capture the river network. However, with the mesh independent, it is possible to use refined mesh near river to capture river features. To this extend, mesh independent enhances the model.

For HexWatershed, as long as the river networks are available, the topological relationship only improve river bed slope. Thus the mesh independent may be more important.