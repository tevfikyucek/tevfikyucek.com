---
layout: post
title: Convert from Matlab logical to double
date: '2012-03-10 05:45:00'
tags:
- matlab
---

If you see the following error message in Matlab,

> First and second arguments must be single or double.

you need to convert logical values to float using _double_ command before operating on them. &nbsp;

    >> x = [-1 1 0] > 0; y = double(x);
    >> whos x y
      Name Size Bytes Class Attributes
    
      x 1x3 3 logical              
      y 1x3 24 double              

<img src="https://hitcounter.pythonanywhere.com/count/tag.svg" alt="Hits">
