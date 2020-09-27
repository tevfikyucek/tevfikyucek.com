---
layout: post
title: Custom "hold all" in Matlab
date: '2012-05-22 02:10:00'
tags:
- matlab
---

One of the useful commands in Matlab is hold which holds the last plot. Hold all is particularly useful, if you have multiple plots and want to use diffirent colors for each. From Matlab's help file:

> hold ALL holds the plot and the current color and linestyle so that subsequent plotting commands will not reset the color and linestyle.

One problem with this is if you have a large number of plots, color will cycle around and there is no way to distinguish between different plots. Furthermore, you can only use color feature to distinguish between different plots.

A more intelligent way is to define custom line types in an cell array. Here is an example..

    m1 = {'r', 'g', 'b', 'c', 'm', 'k', 'y'};
    m2 = {'r*--', 'g*--', 'b*--', 'c*--', 'm*--', 'k*--','y*--'};
    figure(1); hold;
    for p = 1:7
    	plot(x(p,:), y(p,:), m1{p});
    	plot(x(p,:), z(p,:), m2{p});
    end

You can change _m1_ and _m2_ cell arrays the way you like.. Just type _help plot_ for other options.

