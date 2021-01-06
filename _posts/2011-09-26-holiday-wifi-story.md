---
title:  Wifi'ing on holiday
layout: post
tags: Holiday, R and R, Story
---

### Open the window and let the wifi in
So for a holiday this year we have decided to go to Devon and have a look around.  So far I am
enjoying the holiday and having a nice restful time.  
But one of the requirements while on holiday was that I have Internet access through wifi or
something.  This was ticked off when the holiday house conformed that they offered wifi access in
the cottage.

### So far so good
Drive over to the cottage and arrive to discover a wifi extender in the cottage offering an open
access point.  Connect and expect no fanfare just access to the Internet but nothing.  Him I
thought what can be wrong...  A tail of the kernel message log shows no DHCP server running.  This
warrants a little more investigation.

### Round 2 static IP goodie
So a look under the box show a class C static IP address of the router that could leave to a working
wifi solution.  Set a static IP on the lappy to be in the same network and be able to talk to the
router.  Bingo communication with the router this is good still no Internet access but I can access
the router and it has been reset to defaults by a previous occupant of the cottage.  I sense a
problem here no wifi access this could be a pain.

### Visit from the landlady
So we have been here about an hour having arrived earlier than anticipated.  The Landlady has notice
either me fiddling with the wifi router or we have arrive and she is just popping over to introduce
herself.  I ask her about the wifi to find out that they don't have much information, their cousin's
daughters lad set it up and it has worked ever since.

### Where did I put my CSI glasses
Ok so if I want Internet for the next 2 weeks it is up to me.  Way-back when I was playing with
Internet whatsit's you needed an up-stream and a down-stream whatsit.  Switch off the router plug in
the hi-gain wifi unit I can see a BT-home hub very interesting and *it* allows me to talk to the
Internet.  But only on the window sill where the wifi router/extender thingo is/was.  Right the
password they gave me allows me to talk to the BT home hub and talk to the Internet.  I sense a
cunning plan hatching.  The BT home hub thingo gives me an IP address that is in the same network as
the wifi router thingo here and the gateway is the same address as the router thingo that is never
going to work well.  After reading the wiki [wireless lan] pages about wifi and the various
configurations I figured that the setup using a repeater combination halving the wifi through-put.
1/2 talking to my devices and 1/2 talking to the BT home hub is the winner.

### All down hill Internet working soon...
This router/extender offerers me 2 options with WDS enabled and without.  It turns out the with
[WDS] disabled is the correct setup to use.  But I am getting a very low signal strength talking to
the BT home hub with anything other that my hi-gain wifi antenna thingo.  This is painful as the
extender can see the BT home hub on a scan but cannot actually talk to it to pass traffic the
counters are not increasing.

### Open the window let the wifi signal in
So after much frustration and its getting warm today I open the window.  Suddenly everything's 
working the traffic counters are counting and the lappy is surfing the Internet through the wifi
extender I can also add my android phone as well.  This is great but what is happening here?  The
walls on the cottage are about 3-feet thick and RF is attenuated so badly that there is no signal.
My phone can atest to this as I walk around inside that the signal goes to 0.  The window where all this is
happening is on the same side of the house as the BT home hub.  But it is at the very edge of the
range some days window closed signal is fine.  Other days I have to open the windows to get get a
signal.  I'm guessing here that the RF signal is attenuated enough that some days are good and some
days are bad for a holiday judgement open the window to surf the Internet.

[wireless lan]: http://en.wikipedia.org/wiki/Wireless_LAN
[WDS]: http://en.wikipedia.org/wiki/Wireless_distribution_system

