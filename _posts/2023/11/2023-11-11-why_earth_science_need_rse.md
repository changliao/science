---
title: What prevent us from learning new programming skills
date: '2023-11-11'
permalink: /posts/2023/11/11/why_earth_science_need_programming_training
author: Chang Liao
tags:
- ESM
- Software
- Programming
---

A couple of days ago I ran into a Twitter post:
https://x.com/_VincentS_/status/1722674693616910450?s=20


![Figure 1](https://github.com/changliao/science/blob/main/_figures/programming/github.jpeg?raw=true)

Although I recently turned to Bluesky for social network (https://bsky.app/profile/changliao.bsky.social).

If you are able to open the Twitter post with the figure, you might wonder what is the intension of this post. There are a few comments of this post as well. There are some quick takeaway based on my understanding. First, there are developers who don't actually write code, but might provide suggestion to other developers. There are also developers who delicate time to actually write the code. One of the comments also pointed out some GitHub activities are also **fake** because they are not actually programming activities, but instead spell checks. This reminds me that there are also people buy GitHub stars for some purposes.

I am from the academic background, so this somehow reflect some reality. Most senior modeling researchers do not code or don't even have a GitHub account yet they still claim they are modelers. In contrast, a PhD/postdoc, or early career scientist may still get involved in programming activities. Thus their GitHub profile may actually resemble the lower part of the figure.

So what prevent senior modelers from coding? My experience and observation provide me with several explanations:
1. Senior modelers simply don't have time for programming. Some of them are busy with proposal and team building, often have to lend heavy lifting to early careers. Especially if you consider the technology of GitHub is quite new, many modelers came to fame before GitHub was born.
2. Senior modelers actually don't have the coding skills. This is also possible because many modelers are more mathematical-based, or equation-based, and have less experiences in computer programming.
I have also seen peers use Excel for modeling, which is quite different from the common modeling practice.
3. Senior modelers stopped learning new skills. I think this might be a deeper problem that most of us ignored.

I will skip reason 1 and 2 because I think reason 3 feels more personally to me. 
My personal experience is that I received most of my programming training during my undergraduate back in 2005-2009. Most of my C/C++ knowledge were taught in classes. I also had some courses taught in MATLAB for image processing for remote sensing dataset.
I self taught IDL (to replace MATLAB) and C# during my master program between 2009-2012. 
I then re-picked up C++ during my PhD 2012-2017.
After PhD, I self taught Python to replace IDL.

Until now, also I use Python and C++ on a daily base, I still feel the limit in my programming skills. Why? because I haven't caught up with latest C++ and Python features. For an Earth scientist, once you found a solution to do a task, you are very often likely to stick with that solution for a long time. This is what we call it habit. I have seen peers use MATLAB and NCL and refuse to switch to Python even though they know NCL will not be supported. 

As a scientist, we are forced to focus on the science, not the process or the solution. 

On the other hand, our advances in high performance computing (HPC) often shield our limit in programming skills. I have also seen peers wrote inferior performance code and run it on HPC. 
If a code take a short time run on HPC, then no one will question the code.
If a code take a lots of time to run on HPC, most modelers will just consider this is a computational expensive code. Most of us will not question whether it is because the code was poorly written. That is also why we need FAIR, so peers can help each other to improve the code.

Most organization don't have a mechanism to train scientists to become better modelers. And it completely depends on personal career development. Considering that academia often only reward publications, few and few scientists will invest time on programming. Because in order to stay in the game, they will rather use more expensive computers (larger project funding) or hire early careers to compensate the computational demands. Once an early career becomes senior and have access to more resources, they will also do the same.

