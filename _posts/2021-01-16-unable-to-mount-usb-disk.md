---
title:  Cannot mount USB disk any more
layout: post
tags: Linux, Mint Linux 20, Cinnamon, chrome-remote-desktop
---

## Not authorized to perform operation

I have just pluged a USB flash disk into my mint linux install and it is now telling me I am not authorized to do this.
However it worked yseterday.

I also have installed chrome remote desktop

It seems that there is some weird interaction that prevents me from mounting USB disks.  Thanks to the [Ubuntu Forums] the answer turned out to be:

```
/opt/google/chrome-remote-desktop/chrome-remote-desktop --stop
```

This stopped chrome-remote-desktop from interfearing and means USB disks auto mount again....

[Ubuntu Forums]:https://askubuntu.com/questions/580329/mount-flashdrive-not-authorized-to-perform-operation
