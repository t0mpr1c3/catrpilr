# catrpilr
growing bugs gotta eat

## Description

* Simple snake game written for [BBC micro model B emulator](https://bbc.godbolt.org)
* Entry for [**2019 BASIC 10 liner contest**](http://gkanold.wixsite.com/homeputerium/kopie-von-basic-10liners-2018) in category **PUR-80**

## How to play

**A** up  
**Z** down  
**<** left  
**>** right  

## Code summary:

Line 0.
*	Initialize screen and variables.
*	Run only once

Line 1.
*	Show high score at end of previous game
*	Start new game

Line 2.
*	Lose life, make death sound, pause

Line 3.
*	Draw game box
*	Set up variables for next round

Line 4.
*	Make score sound, randomly select location of target

Line 5.
*	Update score and number of lives, print status bar

Line 6.
*	Get keyboard input 'A' up, 'Z' down, '<' left, '>' right

Line 7.
*	Make move sound

Line 8.
*	Update location indices for head and tail
*	Get pixel colour at next location 

Line 9. 
*	Print head and neck,blank out vacated tail location
*	Depending on pixel colour GOTO line 2 (yellow/blue=dead), 4 (red=target), 6 (empty cell)

## Variables:

**L.** constant 467 = x-location of left side of box  
**R.** constant 851 = x-location of right side of box  
**T.** constant 1011 = y-location of top side of box  
**B.** constant 627 = y-location of bottom side of box  
**a.** x location of target / value 1305 = VDU code to draw line  
**b.** y location of target  
**c.** constant = 17 VDU code to set colour  
**d.** direction of next move: 2=up, -2=down, 1=left, -1=right  
**f.** flag variable  
**g.** game score  
**h.** high score  
**i.** temporary variable  
**j.** temporary variable  
**k.** constant 31 = VDU code to set cartesian coordinates
**n.** number of lives left  
**o.** constant 13 = x-offset of box  
**p.** pixel colour at next location  
**r.** real length of caterpillar  
**s.** screen length of caterpillar  
**t.** index of tail position  
**u.** index of current position of head  
**v.** index of next position of head  
**w.** wait duration / maximum length of caterpillar / ASCII '*'  
**x.** address of vector of x-locations  
**y.** address of vector of y-locations  
**z.** constant 32 = ASCII space / width of 1 character  
