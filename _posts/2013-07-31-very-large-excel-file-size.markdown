---
layout: post
title: Very large Excel file size
date: '2013-07-31 17:31:00'
tags:
- excel
- engineering
---

I've recently received an Excel file which only had ~140 rows and 10 columns in a single sheet. I was surprised to see that the filesize was 10 megabytes for this file. I've searched for images for raw data in the document but there was not any. Searching in the web, I found the problem. The sheet had lots of rows (~65000) which were part of the file but was also simply empty.

To remove the unused rows, I've used "_CTRL+END_" to go to the last row and deleted all unused rows. Please note that you need to delete the rows, simply clearing/cleaning the rows does not reduce the file size. After saving the file, the size was reduced to 81 kilobytes only.

