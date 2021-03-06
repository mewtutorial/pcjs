---
layout: page
permalink: /
machines:
  - type: pc
    id: ibm5150
    config: /devices/pc/machine/5150/mda/64kb/machine.xml
  - type: c1p
    id: demoC1P
    config: /devices/c1p/machine/8kb/large/machine.xml
---

Welcome to [PCjs](/docs/about/pcjs/), the first IBM PC simulation to run in your web browser without any plugins.
It was added to the [JavaScript Machines](/docs/about/) project in Fall 2012, and it is now part of the
[PCjs Project](https://github.com/jeffpar/pcjs) on [GitHub](http://github.com/).  The project includes:

* [PCjs](/docs/pcjs/), a simulation of the original IBM PC (circa 1981)
* [C1Pjs](/docs/c1pjs/), a simulation of the OSI Challenger 1P (circa 1978)

All the simulations are written entirely in JavaScript.  No Flash, Java or other plugins are required.
Supported browsers include modern versions of Chrome, Safari, Firefox, Internet Explorer (v9.0 and up), Edge,
and assorted mobile browsers.

{% include machine.html id="ibm5150" %}

The [simulation](/devices/pc/machine/5150/mda/64kb/) above features an Intel 8088 running at 4.77Mhz,
with 64Kb of RAM and an IBM Monochrome Display Adapter.  For more control, there are also
[Control Panel](/devices/pc/machine/5150/mda/64kb/debugger/) and [Soft Keyboard](/devices/pc/machine/5150/mda/64kb/softkbd/)
configurations, featuring the built-in PCjs Debugger.  For even greater control, build your own PC. The
[PCjs Documentation](/docs/pcjs/) will help you get started.

The goals of the [JavaScript Machines](/docs/about/) project are to create fast, full-featured simulations of classic
computer hardware, help people understand how these early machines worked, make it easy to experiment with different
machine configurations, and provide a platform for running and analyzing old computer software.

Demos
---
Some pre-configured machines are shown below, ready to run BASIC, DOS, Windows 1.01, and assorted non-DOS software.

{% include screenshot.html src="/devices/pc/machine/5150/cga/64kb/donkey/thumbnail.jpg" width="200" height="120" title="IBM PC running DONKEY.BAS" link="/devices/pc/machine/5150/cga/64kb/donkey/" %}
{% include screenshot.html src="/devices/pc/machine/5160/cga/256kb/demo/thumbnail.jpg" width="200" height="120" title="IBM PC XT w/CGA, 10Mb Hard Drive" link="/devices/pc/machine/5160/cga/256kb/demo/" %}
{% include screenshot.html src="/devices/pc/machine/5160/cga/256kb/win101/thumbnail.jpg" width="200" height="120" title="IBM PC XT w/CGA, Windows 1.01" link="/devices/pc/machine/5160/cga/256kb/win101/" %}
{% include screenshot.html src="/devices/pc/machine/5160/ega/640kb/win101/thumbnail.jpg" width="200" height="120" title="IBM PC XT w/EGA, Windows 1.01" link="/devices/pc/machine/5160/ega/640kb/win101/" %}
{% include screenshot.html src="/disks/pc/os2/ibm/1.0/thumbnail.jpg" width="200" height="120" title="IBM PC AT w/EGA, OS/2 1.0" link="/disks/pc/os2/ibm/1.0/" %}
{% include screenshot.html src="/disks/pc/cpm/1.1b/thumbnail.jpg" width="200" height="120" title="IBM PC w/MDA, CP/M-86" link="/disks/pc/cpm/1.1b/" %}
{% include screenshot.html src="/disks/pc/games/microsoft/adventure/thumbnail.jpg" width="200" height="120" title="IBM PC w/MDA, Microsoft Adventure" link="/disks/pc/games/microsoft/adventure/" %}
{% include screenshot.html src="/disks/pc/games/infocom/zork1/thumbnail.jpg" width="200" height="120" title="IBM PC w/CGA, Zork I" link="/disks/pc/games/infocom/zork1/" %}

Check out the rest of the PCjs [Application](/apps/pc/), [Boot Disk](/disks/pc/) and [Machine](/devices/pc/machine/)
demos, including an [IBM PC Dual Display System](/devices/pc/machine/5150/dual/64kb/) demo of multiple monitor support,
and [IBM PC XT "Server Array"](/devices/pc/machine/5160/cga/256kb/array/) and [Windows 1.01 "Server Array"](/devices/pc/machine/5160/ega/640kb/array/)
demos of multiple machines running side-by-side.

C1Pjs
---
Below is the [OSI Challenger C1P](/docs/c1pjs/), another simulation in the JavaScript Machines project.
It simulates Ohio Scientific's 6502-based microcomputer, released in 1978.  More details about this simulation
and the original machine are available in the [C1Pjs Documentation](/docs/c1pjs/).

{% include machine.html id="demoC1P" %}

License
---
The [PCjs Project](https://github.com/jeffpar/pcjs) is now an open source project on [GitHub](http://github.com/).
All published portions are free for redistribution and/or modification under the terms of the
[GNU General Public License](/LICENSE) as published by the Free Software Foundation, either version 3 of the License,
or (at your option) any later version.

You are required to include the following copyright notice, with a link to [{{ site.pcjs.domain }}]({{ site.url }}/):

> [PCjs]({{ site.url }}/) © 2012-2016 by [Jeff Parsons](mailto:Jeff@pcjs.org) ([@jeffpar](http://twitter.com/jeffpar))

in every source code file of every copy or modified version of this work, and to display that notice on every web page
or computer that runs any version of this software.

See [LICENSE](/LICENSE) for details.

More Information
---
Learn more about the [JavaScript Machines](/docs/about/) Project and [PCjs](/docs/about/pcjs/).  To
create your own PCjs machines, see the [Documentation](/docs/pcjs/) for details.

If you have questions or run into any problems, feel free to [tweet](http://twitter.com/jeffpar) or
[email](mailto:Jeff@pcjs.org).
