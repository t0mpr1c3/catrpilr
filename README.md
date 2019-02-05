# catrpilr
Growing bugs gotta eat.

## Description

* Simple snake game written for the javascript BBC micro model B emulator, [jsbeeb](https://bbc.godbolt.org/).
* Entry for [**2019 BASIC 10 liner contest**](http://gkanold.wixsite.com/homeputerium/kopie-von-basic-10liners-2018) in category **PUR-80**

## Features

* Fast, playable action!  
* Bleeps! Flashing lights! High score!  
* _Special bonus screen memory glitches!_

I don't know what causes the on-screen garbage: it might be something to do with how the emulator is implemented.

## How to play

Download CAT80.zip from the [github repo](https://github.com/t0mpr1c3/catrpilr/raw/master/CAT80.zip) and extract the virtual disk `CAT80.ssd`. Upload the file into *jsbeeb*, or an offline emulator such as [BeebEm](https://en.wikipedia.org/wiki/BeebEm), and type `CHAIN "CAT80"`. 

(Note that *jsbeeb* has a funky keyboard mapping: on my US keyboard I got the double quote by typing `SHIFT-2`.)

Alternatively, copy/paste the BASIC code into the console of *BeebEm* and type `RUN`.


#### Controls:

  **A** up  
  **Z** down  
  **<** left  
  **>** right  
  
#### Tips:

* Move around the caterpillar box eating the tasty red food that helps you grow.  
* Try not to bite your own tail or crash into the side of the box. That's like, ouch.  
* Look out for the power pills! For 10 seconds you will move extra quick, and score more points for all the food you eat.

## Code summary:

Line 0.
*	Initialize screen and variables
*	Run only once

Line 1.
*	Show high score at end of previous game
*	Start new game

Line 2.
*	Lose life, make death sound
* Update number of lives in status bar
*	Set up variables for next round

Line 3.
* Pause before next round
*	Draw game box

Line 4.
*	Update score
*	Make happy sound

Line 5.
* Randomly select location of next target
* Print score in status bar

Line 6.
*	Get keyboard input
* 'A' up, 'Z' down, '<' left, '>' right

Line 7.
* Repeat keyboard input for the appropriate amount of time
*	Make move sound
*	Update location index for head

Line 8.
*	Update location index for tail
*	Get pixel colour at next location 

Line 9. 
*	Print head and neck, blank out vacated tail location
*	Depending on pixel colour GOTO line 2 (yellow/blue/outside box=dead), 4 (red=target), 6 (black=empty cell)

## Variables:

**a.** x location of target / value 18 = VDU code for GCOL   
**b.** y location of target / value 13 = y-location of status bar
**c.** colour variable indicating pixel colour at next location: -1 = outside box, 0 = black, 1 = red, 2 = yellow, 3 = blue  
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
**q.** flag variable: 0 = normal speed, -1 = whoosh! you just ate a power pill  
**r.** real length of caterpillar  
**s.** screen length of caterpillar  
**t.** index of tail position  
**u.** index of current position of head  
**v.** index of next position of head  
**w.** wait duration / value 120 = ASCII `x`  
**x.** address of vector of x-locations / value 1028 = 10.28 seconds duration of power pill effect 
**y.** address of vector of y-locations   
**z.** constant 380 = x/y location of top left corner of box  
**T.** most recent value of TIME  
**U.** value of TIME after last move  
**X.** direction of next move: 1=left, -1=right  
**Y.** direction of next move: 1=up, -1=down 

## Cheats

* **Infinite lives:** Remove `n=n-1:` at the beginning of line 2  
* **Longer caterpillar:** Change `r=5` in line 1 to `r=10` or some other value  
* **Faster game:** Change the inequality in line 7 from `T>U+40-r+10*q` to, say, `T>U+30-r+10*q`
