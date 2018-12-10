# MF70-CNC
Proxxon MF70 mill CNC conversion

This project is for my conversion of a Proxxon MF70 mill to CNC. The contents will be mostly config files, scripts, improvement designs, as well as a list of various information I found useful.

This is mostly for my own use, but I hope somebody else will wander into it and save some time.

## Why

It's small and cheap, that's really about it. Before spending the time, effort and money on a larger, much heavier and expensive machine, I decided to start small and see whether I like this stuff at all. So far I do.

It has to be said that the mill is *tiny* and extremely limited in what it can do. But it can be made work.


## Conversion process

The mill was converted using the 3D printed parts from the "Bubblegum CNC" project, and can be found at https://www.thingiverse.com/thing:33799

There are assembly videos at https://www.youtube.com/watch?v=zhckeUoXwuc&list=PLYxf6JVpXtyO_PyjGGxkbttEl6JiWM5uO

I found both to work fine without much of an issue.

I didn't particularly like the idea of gluing endstops to the plastic -- seems flimsy, but it does work.

The plastic parts proved sturdy enough to resist the mill trying to exceed the travel limits -- which is good, but probably not a great thing for the Delrin nuts the machine uses.


## Things I learned

1. CNC coordinates are different from 3D printer coordinates. 3D printers always use positive X, Y and Z coordinates. CNC machines have a 0,0,0 in the center of the table, and positive at one end, and negative at the other. https://www.autodesk.com/products/fusion-360/blog/cnc-coordinate-system-made-easy/
2. You must have endstops on both sides -- so six of them.
3. Make sure the end stops and the movement directions are correctly wired and set -- if during homing towards +X, the motor runs backwards and hits the -X endstop, it will keep trying instead of stopping.
4. For safety, the endstops should be of the normally closed type -- but a common arduino CNC board has revisions that don't support this
5. While 3D printers have long been self-contained machines with a microcontroller that does all the work, it's still common to have a PC make the actual decisions about moving the motors. The microcontroller based solutions like GRBL and Smoothie are less developed.
6. Linux software for microcontroller based CNC is sub-par, and needs improvement. I'm currently trying bCNC.
7. When homing, move the Z axis upwards first, to make sure it doesn't crash into anything
8. Milling is a good deal more work than 3D printing.

## Smoothieware

I mostly went with Smoothieware because it runs on a higher end board -- making more room for CNC functionality, which is more complex than a 3D printer. Unfortunately it's not as well supported as the Arduino based GRBL.


## TODO

1. Rewrite the machine to use NC switches. Currently using NO mostly due to a previous conversion attempt.
2. Fix bCNC to work properly with Smoothieware.
3. Figure out manual tool changes.
4. Try to extend the Y axis by milling replacement parts: https://0xfred.wordpress.com/2012/04/17/extending-the-mf70s-y-axis/
5. Buy a bigger machine.


