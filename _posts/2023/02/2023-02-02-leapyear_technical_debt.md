---
title: Leap year and technical debt
date: '2023-02-02'
permalink: /posts/2023/02/02/leap-year-and-technical-debt
author: Chang Liao
tags:
- ESM
- Software
---

In my work, I need to convert an `E3SM` model output into a different format. The output file is in the `netCDF` and I found some interesting design issue in the model.

The model runs at some time step but the output can be in a different time step. For example, the model can run at 3-hour time step but the output may be daily, monthly.

These are controlled by several namelist variable. However, The model cannot handle the different number of day in different months, which is also relevant to the leap year.

As a result, some of the output time series has 360 days (12 * 30), some 365 days, and some 366 days. In my opinion, this is a typical technical debt which I learned recently. 

This type of design makes the postprocessing and exchange with other workflow extremely difficult. For example, the `time` variable within the netcdf is used to index the time series. And this variable may start from 0 or 1, and the length is also variable.

Ideally, we should use the exact number of days throughout the whole model so they are consistent in all processes.

Now with this issue, lot of `guessing` efforts are needed because the output is simply unusable. 

Reference: https://en.wikipedia.org/wiki/Technical_debt
