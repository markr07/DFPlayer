
Three Ways to Add Sound Objects to a Model Railroad with DFPlayer


Using An Arduino Mega Running DCC-EX EX-Command Station
or for Traditional Layouts, Incorporating Simple Switches and Relays

Document last revised 250913

The DFPlayer Dual Caddy (MCU)
<img width="576" height="432" alt="image" src="https://github.com/user-attachments/assets/6692ce81-8c8a-4612-96b0-6aea48f527c2" />

The DFPlayer Dual Caddy for All
<img width="627" height="432" alt="image" src="https://github.com/user-attachments/assets/d707ec46-393a-447d-85fc-bf1f42270444" />

DFPlayer USE Matrix

What happens if one wants more than two DFPlayers?  Under DCC-EX EX-Command Station, serial port expansion is an option but requires the help of the I2C bus with several additional hardware considerations.  

The DFPlayer has three operating modes; 
Serial Communications
Direct I/O
Loop

Commonly available positive level triggered opto-isolated relay boards designed to be driven by MCUs can simulate both short and long momentary button depressions or a latching switch.  Solid State Relays and sensors can also be employed.

Assuming the sound object requires only one or few different clips, operating the DFPlayer in either Direct I/O mode or Loop mode can be a viable alternative.  There are instances where one or two clips Is all that’s necessary for a given detail.  In Loop mode, a single audio clip playing the sound(s) of burning wood in concert with the respective associated campfire lighting detail can work well and save the MCU’s serial ports for sound objects that require many clips, regardless of order and at a variety of volume levels.  

<img width="882" height="285" alt="image" src="https://github.com/user-attachments/assets/7fbf5c8b-18f8-44d7-a20e-7c1f532844e9" />



