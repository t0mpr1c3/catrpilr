# catrpilr
snake game in 10 lines of BASIC

## Description

* Simple snake game written for [BBC micro model B emulator](https://bbc.godbolt.org)
* Entry for [**2019 BASIC 10 liner contest**](http://gkanold.wixsite.com/homeputerium/kopie-von-basic-10liners-2018) in category **PUR-80**

## How to play

**A** up  
**Z** down  
**<** left  
**>** right  

## BASIC code:

```
0V.278;23;8202;0;0;0;787;6;0;:g=0:h=0:k=31:o=13:u=1:w=0:x=&C00:z=32:B=851:T=1011
1n=4:p=0:s=9:w=3*w:f=g>h:h=h-f*(g-h):g=0::L=467:R=627:IFh P.TAB(17,6)"H!_5[*r="
2n=n-1:V.k,o+n,o,z,k,o+x?u,y?u,120*p:SO.0,-9*p,7,9:TI.=0:REP.U.TI.>2*w:IFn=0TH.1
3a=1305:V.12,25,4,L;T;a;R;T;a;R;B;a;L;B;a;L;T;:d=2:p=0:r=0:w=42:y=x+w:?x=6:?y=6
4F.i=0TOp:SO.0,-4*p,i,1:N.:REP.:b=a:a=RND(11):U.PO.L+z*a,T-z*b)=0:g=g+5*p
5c=17:V.k,o+a,b,36,k,o,o,w,w,w,k,o+n,o,z,z,529;k,c,o:P.g:s=s-p/2*(s<41):TI.=0
6v=(u+1)MODw:REP.:i=INKEY-104-INKEY-103:j=INKEY-98-INKEY-66:IFi d=i EL.IFj d=2*j
7U.TI.>5A.TI.>25-r:TI.=0:i=ABSd:j=u A.1:SO.0,-5,j+1,1:t=(v-s+w)MODw:f=r=s
8s=(s-f)MODw:x?v=x?u+d*(i=1):y?v=y?u+d/2*(i=2):p=PO.L+z*x?v,T-z*y?h):p=p+(p=3)
9V.c,j+1,k,o+x?u,y?u,64,c;k,o+x?t,y?t,z*f,c,1,k,o+x?v,y?v,120-z*j:u=v:G.(6-2*p)
```

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
**R.** constant 627 = x-location of right side of box  
**T.** constant 1011 = y-location of top side of box  
**B.** constant 851 = y-location of bottom side of box  
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
