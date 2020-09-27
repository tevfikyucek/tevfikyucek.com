---
layout: post
title: Plotting X-axis in Reverse Order in Matlab
date: '2011-06-02 06:36:00'
tags:
- matlab
---

In Matlab, x-axis goes from smaller values to larger values. This is true irrespective of the order of values in the x-axis matrix used in plot command. I needed to revert the values in axis so that I can visually compare data with results from excel. Here is how to achieve this:

    ha = gca;
    set(ha, 'xdir', 'reverse');

<img src="https://hitcounter.pythonanywhere.com/count/tag.svg" alt="Hits">
