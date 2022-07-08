---
 
title: Break the model
date: '2022-01-02'
permalink: /posts/2022/07/08/break-the-model
author: Chang Liao
tags:
- Modeling
---

Recently I have broken a few models I wrote previously into pieces, which gave me lots of thoughts on how I, as a modeler, work to improve our modeling skills.

Most of the times, we think modelers are just scientists turning equations into code and key part of this activity is how to formulate the equations, which is the science part.

In reality, model development involves lots of activities more than just the equations. Other activities are model design, data I/O, visualization, for example. Along this path, modelers often have to make lots of decisions, some are more critical than the other. 

I am by no mean a computational scientist, but I know when a computer scientist designs a programming language, he/she needs to make a decision when an array index should start with 0 or 1. This sounds trivial from a language user's perspective, but its consequence on the language designer is not. Similarly, a modeler often have to take a similar path, making decisions as we keep improving the models. However, sometimes we may realize that some decisions we made earlier were not good enough, which could potentially limit the ceiling of the models. This is the time we have to consider a breakup, break the model into pieces and rebuild.

One example is when I developed the hexwatershed model. In the beginning, I needed to run the model at the watershed scale although the ultimate goal is global scale. So when I designed the function to calculate distance I used the classical Euclidean distance equation, which requires two sets of X and Y coordinates. This method works fine at regional scale because X/Y can be obtained using a map projection. However, when I moved to global scale, I immediately found that I can no longer use projections because the GCS system is preferred at global scale. In the end, I rewrote the whole geometry related equation using the GCS, which is universal at any scale. Breaking a model is a both a challenging and rewarding process. Through this process, we can gain a better understanding what could have done better and what we can learn from it. 

The most difficult challenge is not writing the pieces of code, it is where to break and how to find the minimal component the model should have. As they say the perfect program is not that there is anything to add to it, but nothing should be removed from it. Writing the program that has less dependency, easy to expand, and align with our scientific understanding should be our goal.

We are often trained to solve a big problem and we are good at providing a big solution that includes everything. Sometimes the beauty of a solution is not the solution itself, but it lies in itself flow. It is like building a house, the beauty of a house is not just itself, but its capability to be customized such as adding or removing some components from it. A house blueprint map that can be used to generate hundreds of different houses is a beauty.

