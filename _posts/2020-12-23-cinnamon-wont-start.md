---
title:  Cinnamon wont launch
layout: post
tags: Linux, X windows, Mint Linux 20, Cinnamon
---

## Cannot launch cinnamon anymore

I get this error message:

```
Unable to launch "cinnamon-session-cinnamon" X session...
"cinnamon-session-cinnamon" not found falling back to default session.
```

I found this in the [Mint Linux forums]

* Check the disk for errors.
No errors were found or found and fixed.

### The eventual fix
Reboot into recovery and enabled networking.

Then run the following commands:
```
mount -o remount,rw /
apt update
apt install --reinstall cinnamon
sync
reboot
```

_NOTE_: I missed of the last to steps as I did this via the recovery console and just went back to recovery console and booted Linux normally.

[Mint Linux forums]: https://forums.linuxmint.com/viewtopic.php?t=278084
