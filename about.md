---
layout: page
title: About
permalink: /about/
---

Teamboyce Labs is based in Cambridge UK.  With over 20 years experience working
on embedded systems ranging from 8-bit micro-controllers to 32-bit and 64-bit
Embedded Linux systems.

Specialising in device drivers, boot loaders, BSP, and build systems. 

## Experience

Below are some of the projects and technologies that was worked with.

### Olimex l9260 simple ADC driver

While working on an embedded Linux project using an [Olimex L9260] board.  A method to be able to 
read from the 2 ADC channels with minimal effort as hi-speed sampling was not a requirement.
This required a simple kernel driver to make both ADC channels available to a user space application.

[Olimex L9260]: http://www.olimex.com/dev/sam9-L9260.html

### Embedded Linux build system

A small and simple Linux build project that can produce a complete Linux root file system for an 
embedded device.  This involved taking the SDK provided by the chip vendor.  In this case 
STLinux 2.3 and create an embedded system that is easy to modify and easy to re-target.  There are 
a number of external tools that are capable of doing this, having used many of these system in the past
([Buildroot], [Open Embedded], [Scratchbox], [OpenWRT]) they were all considered too big for this 
project.  Instead a smaller system that is based around the [kconfig] system used in a 
number of open source projects.  Using this and GNU make a system was quickly put together that is
retargetable and able to create a very small root file systems without much effort.  This system
uses [busybox] for the shell and all core Linux applications. Then using udev for auto-mounting
of USB disks and IP network connection via RNDIS devices udev scripts to keep the size down.

[Buildroot]: http://buildroot.uclibc.org/
[Open Embedded]: http://openembedded.org/index.php/Main_Page
[Scratchbox]: http://www.scratchbox.org/
[OpenWRT]: https://openwrt.org/
[kconfig]: http://www.kernel.org/doc/Documentation/kbuild/kconfig-language.txt
[busybox]: http://www.busybox.net/

### HTTP Firmware upgrade

One requirement of this project was the ability to firmware upgrade over a wireless link and via a 
USB DISK in the factory.  Once the initial system was created with [busybox] the httpd daemon was added
to this configuration to enable firmware to be pushed to the system using an http post message.  
The system would then replace the main image root file system and the Linux kernel.  Again udev
scripts were enhanced to perform the network connectivity and prompt firmware upgrade on USB disk
insertion.

[busybox]: http://www.busybox.net/

### LPC9XX ISP to ICP bridge

Having work on the Philips and latter the NXP LPC900 series micro-controllers I had written a 
serial base [programmer (lpc935Prog)] for these chips using a PC serial port and some specific 
timing to enter ISP mode.
But as time has marched forward and serial ports are harder to get on PC's these days, another
approach is required.  There is already open source software for this so what was required was a
hardware platform that would easily perform the HW requirements to enter programming mode and then
program the chip either in-circuit or stand-alone.

[programmer (lpc935Prog)]: https://github.com/rodb70/lpc935prog

### DMX LED light controller

Having some experience in stage rigging, a project was created to work on the design for
a multi-channel LED light.  The requirements were simple a multi-channel LED based light that could
be used as a coloured flood in small environments.  While there are many reasonable priced led
based light in this space that would fit the requirements.  The challenge is in the journey
to look at these LED lights and see what could be improved.
 
### Linux USB hub driver

One project we developed an interface between their already existing embedded Wireless USB
host controller to the Linux and a USB hub.  This turned out to be a reasonably straight forward
task of mapping normal events that happen on a USB hub to events that happen on a Wireless USB
system.  For example the USB event of unplugging a device from a workstation.  Can be mapped onto
a Wireless USB device being switch off or moving out of range.  In wireless USB there is an
authentication step that must occur before the device is allowed to connect to the workstation.
This means that we have to put off telling the operating system that a device has been connected
to the hub until this authentication step is complete.  This was made more complicated due to the
fact that there were 3 different projects with this and we had to be able to compile this for 3
different Linux kernel versions without any source code changes.  This involved setting up a new
set of build targets that could build this driver and associated files.

### Advanced Make systems

Advanced experience using makefile base build systems.  Using a paper called
[Recursive Make Considered Harmful] we development / improved a number of 
embedded build systems.  This has culminated in a project to develop of a
simpler more generic build system.  This project can replace almost any build
system to speed up development for existing embedded projects.

In some cases build times have decrease from 40-minutes per build to less than
5-minutes per build.

[Recursive Make Considered Harmful]: http://miller.emu.id.au/pmiller/books/rmch/

### 8 segment LED readout

Originally designed as a large object counter moving through a gate.  This design was re-purposed
for another project as a delay timer for a heating system, able to be programmed upto 99 hours in advance.
Given the available timer/counters on the P89LPC935 this project could be altered to fit a number of
simple instrument needs.

### Battery backed-up low-voltage device

This device is mostly mains-powered device that had a low-voltage ni-cad battery backup.
The device contained a peek-detect ni-cad battery charger with a dis-charge and recharge cycle build
in to preserve the batteries as long possible.

### Contact me

[developer at Team Boyce dot com](mailto:email@domain.com)
