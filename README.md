# catrpilr
growing bugs gotta eat

## Description

* Simple snake game written for [BBC micro model B emulator](https://bbc.godbolt.org)
* Entry for [**2019 BASIC 10 liner contest**](http://gkanold.wixsite.com/homeputerium/kopie-von-basic-10liners-2018) in category **PUR-80**

## How to play

Upload the virtual disk `CAT80` into the emulator, and type `CHAIN "CAT80"`.

#### Controls:

  **A** up  
  **Z** down  
  **<** left  
  **>** right  

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

**a.** x location of target / value 1305 = VDU code to draw line  
**b.** y location of target  
**c.** constant 435 = x-location of left side of box   
**d.** constant 1011 = y-location of top side of box    
**e.** direction of next move: 2=up, -2=down, 1=left, -1=right  
**f.** flag variable  
**g.** game score  
**h.** high score  
**i.** temporary variable  
**j.** temporary variable  
**k.** constant 31 = VDU code to set cartesian coordinates  
**m.** constant 42 = maximum length of caterpillar / ASCII `*`  
**n.** number of lives left  
**p.** pixel colour at next location  
**q.** constant 13 = x-offset of box  
**r.** real length of caterpillar  
**s.** screen length of caterpillar  
**t.** index of tail position  
**u.** index of current position of head  
**v.** index of next position of head  
**w.** wait duration / value 120 = ASCII `x`
**x.** address of vector of x-locations  
**y.** address of vector of y-locations  
**z.** constant 32 = ASCII space / width of 1 character  
