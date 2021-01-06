---
title: Ignoring error codes at our expense
tags: Error codes,
---

## Ignoring Error codes is bad for your code

While working and maintaining a piece of code.  I came across a well worn issue 
that keeps popping up.  There are functions we are calling into that return
error codes and for whatever reason we are choosing to ignore these codes.

Is that a good thing or a bad thing?

Well it depends on your point of view if this is a user space application then
perhaps it does not matter.  But if this is the rocket motor on a satellite or
the Xray off control for a new medical instrument we should check the error codes.

I would propose that aside from these two extremes there are many other times when
error codes should also be checked.  

### Case 1 - Boot loader crashing when trying to read a file
While looking into this, the boot loader would just crash and revert back to the
on-chip boot loader.  This would cause the output to say unhandled interrupt and
reboot the board.

Adding a few more prints and tracking the path through the code showed that the
cause of this problem to be trying to read a file from an unmounted file system.

But the real cause was not the unmounted file system but the ignored error
returned when mount failed.

### Case 2 - Application dies with SIGSEGV
This one is interesting as the main application dies with the error SIGSEGV.
Again following the path the code takes showed a standard path and nothing
unusual.  But after rebuilding and looking at the warnings from the compiler
it was clear that the issue here was not enough parameters to printf.

While this was a warning from the compiler it is still a good reminder that
all warnings and errors produced by our tools should be investigated and removed
from our code.

### In the end

I would also be a strong proponent of making the compiler as sensitive as
possible.  Turn warnings into errors and make the compiler stop for all of them.

