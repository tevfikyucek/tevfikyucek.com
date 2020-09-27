---
layout: post
title: Transparent Graph Legends in Matlab
date: '2010-04-28 04:51:00'
tags:
- matlab
---

One thing that started to bother me is that the legends can cover the whole (sub-)figure if I plot many lines in the same figure. It seems it is possible to make legends "transparent" and get rid of the border around the legend box. The following piece of code is very useful:

    legend('boxoff');

_Boxoff_ both makes the legend transparent and removes the border around legends.

More detailed information on how legend's type can be manipulated can be found [here](http://www.mathworks.com/access/helpdesk/help/techdoc/ref/legend.html).

