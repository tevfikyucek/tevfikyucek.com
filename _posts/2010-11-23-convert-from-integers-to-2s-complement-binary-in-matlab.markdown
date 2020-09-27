---
layout: post
title: Convert from Integers to 2's Complement Binary in Matlab
date: '2010-11-23 07:43:00'
tags:
- matlab
---

Here is how to convert from decimal numbers to binary 2's complement in Matlab:

    binary_value = dec2bin(mod((dec_value),2^N),N);

where N is the bit-width of binary number.

<img src="https://hitcounter.pythonanywhere.com/count/tag.svg" alt="Hits">
