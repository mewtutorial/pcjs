---
layout: post
title: Compaq DeskPro 386
date: 2015-02-22 11:00:00
category: 80386
permalink: /blog/2015/02/22/
machines:
  - type: pc-dbg
    id: deskpro386
    config: /devices/pc/machine/compaq/deskpro386/ega/2048kb/machine.xml
    uncompiled: true
---

I finally dumped the [Compaq DeskPro 386/16 ROMs](/devices/pc/bios/compaq/deskpro386/) from the motherboard I bought
on ebay last year, so I'm ready to begin adding 80386 support to PCjs.

I'd also like to locate a copy of the "Compaq DeskPro 386 Technical Reference Guide, Volumes 1 and 2".  It's not hard
to find Compaq Maintenance and Service guides online, but their Technical Reference guides are much rarer, perhaps because
they were expensive ($149) and not many were sold.  Anyway, I'm hoping to either borrow or buy a copy, and then scan and
post it.

A [Compaq DeskPro 386](/devices/pc/machine/compaq/deskpro386/ega/2048kb/) test configuration is displayed below.
The configuration doesn't run, and the debugger can't disassemble 80386-specific code yet, but this is what I will be
using to test and debug my changes over the next few months.

{% include machine.html id="deskpro386" %}

*[@jeffpar](http://twitter.com/jeffpar)*  
*February 22, 2015*
