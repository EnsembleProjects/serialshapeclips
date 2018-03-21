# serialshapeclips

You just send daisy chain them by serial port (RX to TX), make sure all the grounds are connected.

Then send them a string over like this (for 2 clips):

F(red),(green),(blue),(height)X(red),(green),(blue),(height)X

So the first shapeclip takes in the message on RX, then removes the first set of values (preceded by F) from the string and adjusts its settings, and spits out the remainder of the string (after the first X, it adds a new F to the start) on TX to the next shapeclip.

They do that until the message is empty. There is little to no error checking or anything as it was hacked together.

Colours are 0-255, height is 0-400 I think.

EG this does 12 clips:

F255,255,255,400X255,0,0,200X34,34,34,34X255,000,000,400X0,0,255,200X34,34,34,34X255,255,255,400X255,0,0,200X0,34,0,34X255,255,0,400X255,255,0,200X34,8,34,34X

To send the message, either use an Arduino, or use a serial converter from a computer then use serial monitor to type in / or processing or some other language. Connect TX on controller to RX on the first and TX from the last to RX on the controller. You should see any remaining messages transmitted back at the end. 

You can make a serial converter out of an Arduino uno hooked to your computer with reset connected to ground.
