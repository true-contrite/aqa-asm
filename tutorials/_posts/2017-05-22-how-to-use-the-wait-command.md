---
layout: post
title: "How to use the wait command"
---

The `wait` command is a _subroutine_, so you must call it like you would with a normal subroutine, i.e.

~~~asm
call wait1000ms
~~~

AQA have included variations of this subroutine which all correspond to specific timings;

~~~asm
wait1ms
wait10ms
wait100ms
wait1000ms
~~~

These should be used in place of TMR/PRE delays since the clock speed of the 28x1 running the AQA specific compiled code does not run at the same clock speed as mentioned in the 28x1 datasheet.
