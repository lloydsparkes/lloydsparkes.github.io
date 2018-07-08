---
id: 87
title: Timetable Converter
date: 2009-09-05T09:29:23+00:00
author: Lloyd Sparkes
layout: page
guid: http://lloydsparkes.co.uk/?page_id=87
---
## What and Why?

Timetable Converter is a Python Script to turn a CSV into a iCal file.

The Main intention for this script is for Computer Science Students at the University of york to beable to generate a iCal from a simple CSV.

This solution isnt perfect as you still need to generate the CSV to begin with, but its a start.

Tested on IronPython 2.0.2 and Python 2.6

## Usage

> ipy TimetableConverter.py

## The Code

The code is fairly simple, and you can download the whole package, including sample CSV [here](http://lloydsparkes.co.uk/files/TimetableConverter.zip)

If you want to modify the format of how Sessions are put into the CSV you will need to modify the following lines (Lines 64-67)

`<br />
#Modify theses line to change description/summary/location depending on your format<br />
#My format is "Summary Location"<br />
sum = item[i].split(' ')<br />
event.add('summary', sum[0])<br />
event.add('location', sum[1])<br />
`