# catrpilr
Growing bugs gotta eat.

## Description

* Simple snake game written for a [BBC micro model B emulator](https://bbc.godbolt.org)
* Entry for [**2019 BASIC 10 liner contest**](http://gkanold.wixsite.com/homeputerium/kopie-von-basic-10liners-2018) in category **PUR-80**

## Features

* Fast, playable action!  
* Bleeps! Power pills! High score!  
* _Special bonus screen memory glitches!_

I don't know what causes some of the the on-screen garbage: it might be something to do with how the emulator is implemented.

## How to play

Download CAT80.zip, either from the [github repo](https://github.com/t0mpr1c3/catrpilr/raw/master/CAT80.zip) or [Google Drive](https://drive.google.com/open?id=15PFjJfnuuaaakjoFXNT2xX38sfp5RlrV) and extract the virtual disk `CAT80.ssd`. Upload the file into the emulator, and type `CHAIN "CAT80"`.

Alternatively, copy the BASIC code and paste into the console of the [BeebEm emulator](https://en.wikipedia.org/wiki/BeebEm) and type `RUN`.


#### Controls:

  **A** up  
  **Z** down  
  **<** left  
  **>** right  
  
#### Tips:

* Move around the caterpillar box eating the tasty red food that helps you grow.  
* Try not to bite your own tail or crash into the side of the box. That's like, ouch.  
* Watch out for the power pills! They will make you move extra quick until you eat something else.  

## Code summary:

Line 0.
*	Initialize screen and variables
*	Run only once

Line 1.
*	Show high score at end of previous game
*	Start new game

Line 2.
*	Lose life, make death sound
* Pause before next round

Line 3.
*	Draw game box
*	Set up variables for next round

Line 4.
*	Make score sound
* Randomly select location of target

Line 5.
*	Update score and number of lives
* Print status bar

Line 6.
*	Get keyboard input
* 'A' up, 'Z' down, '<' left, '>' right

Line 7.
*	Make move sound

Line 8.
*	Update location indices for head and tail
*	Get pixel colour at next location 

Line 9. 
*	Print head and neck, blank out vacated tail location
*	Depending on pixel colour GOTO line 2 (yellow/blue=dead), 4 (red=target), 6 (empty cell)

## Variables:

**a.** x location of target / value 281 = VDU code for PLOT 1,x,y  
**b.** y location of target / value 384 = length and width of box in pixels
**c.** colour variable derived from pixel colour at next location: 1 = blue/yellow, 2 = red, 3 = black   
**d.** constant 32 = ASCII space / width of 1 character  
**f.** temporary flag variable  
**g.** game score  
**h.** high score  
**i.** temporary variable  
**j.** temporary variable  
**k.** constant 31 = VDU code to set cartesian coordinates  
**m.** constant 42 = maximum length of caterpillar / ASCII `*`  
**n.** number of lives left  
**p.** flag variable: 0 = this is normal food, -1 = this food is a power pill  
**q.** flag variable: 1 = normal speed, 2 = whoosh! you just ate a power pill  
**r.** real length of caterpillar  
**s.** screen length of caterpillar  
**t.** index of tail position  
**u.** index of current position of head  
**v.** index of next position of head  
**w.** wait duration / value 120 = ASCII `x`  
**x.** address of vector of x-locations  
**y.** address of vector of y-locations  
**z.** constant 13 = y-location of status bar  
**X.** direction of next move: 1=left, -1=right  
**Y.** 1=up, -1=down 

## Cheats

* **Infinite lives:** Remove `n=n-1:` at the beginning of line 1  
* **Longer caterpillar:** Change `r=5` in line 1 to `r=9`  
* **Faster game:** Change the beginning of line 7 from `U.TI.>5A.TI.>50-r` to, say, `U.TI.>5A.TI.>35-r`
