---
 
title: 'Scientific writing: how to prepare a good image figure'
date: '2016-03-25T14:11:00.001-07:00'
permalink: /posts/2016/03/25/scientific-graphics/
author: Chang Liao
tags:
- Image
- Color
- Figure
- Writing
modified_time: '2016-04-07T05:21:28.363-07:00'
thumbnail: https://1.bp.blogspot.com/-IOeEN7tqSHc/VtoaXC7q5hI/AAAAAAAANNk/GXrSvsrvyBY/s72-c/matrix.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-373319753761247366
blogger_orig_url: https://changliao.blogspot.com/2016/03/scientific-writing-001.html
---

"A picture is worth a thousand words", from Wikipedia, unveils the importance of figures in writing.
There are many types of figures or pictures, and in the field of Earth Science, image figure is one of the most important types.
By image figure, I mean a figure composed of matrix, such as
https://www.ncdc.noaa.gov/sotc/service/global/map-blended-mntp/201601.gif
Link of the image.

![Figure 1](https://github.com/changliao/science/blob/main/_figures/visualization/noaa_land_ocean_temperature.png?raw=true)

(A selfie is also an image, but it is not commonly seen in scientific writing. Although the above figure is taken from the website, it is publication-ready in my opinion.)

So what makes a good  image figure? The figure above actually gives a good example, and we can see what are the principle elements in this figure.
A clear and concise title
An appropriate map projection
A beautiful color bar and data presentation
Adequate description (data source, etc.)
Even without supplementary material, I believe most readers can understand this figure without difficulties.

So where are the challenges?
Usually we can easily prepare the title, projection and description with care. The challenging part is the color presentation of the matrix data.

For example, if the above image is rendered using black and white, I think all of us will be disappointed (this is not photography).
How about other color scale, such as from green to yellow? Maybe not a good idea.
I think now we almost get to the point that colors matter.

We all know that nearly all colors can be decomposed into Red, Green and Blue and there is more than one million colors we can use. But in real life, we seldom need that much.
A commonly used approach to get the best color for the data is using the color table, or the color look up table, through which only a number of colors (usually less than one thousand) are used for mapping.
The selections of these colors are also based on a few approaches. Anyway, we can produce much nicer color tables such as this:


Link of the image.
The above color table contains exactly 200 colors. And if the matrix contains 200 unique values, the image would be perfectly displayed using these colors.



However, most of time, our data has way too many unique values. The stretch method is then used to scale our data before mapping them. There are also a few different stretch methods for different purposes. ArcGIS Map has some detailed explanation of these methods here.

Most of time, a linearly stretch will work, but sometimes, it does not work due to the data distribution.

However, when the data is stretched, we need to be careful with the color table. Because interpretation of the value from the color table need to be stretched as well. In this case, it has become not intuitive for us to guess the value from the map since its color may not be linearly stretched.

Then the classification method comes into the play. If we can classify the matrix data to a few classes, then it would be pretty straight forward to guess the value range from its color. Besides, classification means that we will only have a few colors, usually less than 20.

There are also quite a few methods of classification.
I will leave this work to the readers.

To be continued...