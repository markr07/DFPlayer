A repository for documenting the implementation progress of the DFPlayer.
Two variations depending on application.

Adding Sound Objects to a Model Railroad with DFPlayer


An Arduino Mega Running DCC-EX EX-Command Station
Or Traditional Layouts Incorporating Simple Switches


The DFPlayer Dual Caddy (MCU)

 


The DFPlayer Dual Caddy for All

 



250918
 
Preface
Early this year, I decided to evaluate ways to add sound to my layout for more fun and greater realism.  I also wanted the option to incorporate sound objects regardless of whether the layout is run by a microcontroller (MCU) or is traditional DC.  Sound objects can be added to any layout by employing the DFPlayer’s Loop or Direct I/O modes with momentary or latching switches.

This an overview of the “soup to nuts” process.  It is not all inclusive and the experiences relate to the particular DFPlayer clones chosen.  In-depth coverage is available from a variety of online sources.  Most of the EX-Rail code is “patched together” with minor modification from the DCC-EX website and their Discord channel.  My background is not in programming so there is absolute certainty that better code can be written.  Short Video clips taken at various stages since the beginning are shown t the end in the PowerPoint version to mp4 conversion posted on YouTube.

EX-Rail is the key product differentiator within the EX-CS ecosystem.  EX-Rail enhances yet simplifies control of other EX-CS features as well as a broad range of accessories.  Sound object implementation is no exception.  

A WiFi equipped Arduino Mega running EX-CS provides only two serial ports that are “open for “business.”  

The DFPlayer Dual Caddy (MCU) was built before the “For All” version because the vision or lack thereof, on how DFPlayer, operating in either Loop mode or Direct I/O mode, can provide many more sound objects.  Loop mode operation requires only one digital I/O pin per object; Direct I/O mode only two pins.  A single clip or a few clips can suffice for certain objects.  

Been thinking about adding a campfire to the layout for some time.  “Giving” the campfire” sound without sacrificing one of the two serial ports, already assigned to the Tower and Station, clinched the decision.  The campfire sound object is initially setup to operate in Direct I/O mode and have two sound clips, the primary campfire and a secondary, “howling winds.” 

Another DFPlayer, operated in Loop mode (single clip sound object) will emit howling winds from inside the tunnel.
May decide to add a second tunnel speaker and thereby can change the burning campfire DFPlayer to Loop mode. And, gain a pin for another layout sound object located in a different area.

Two DFPlayers, one assigned to the Tower and the other to the Station, are operated in Serial Communications mode.  The wind clip was added to both because Serial Communications mode allows selection and individual volume level of a single clip among many stored on a micro SD card.  The wind will be coming from all directions.

If more digital pins are needed than the Arduino Mega’s 28 (defined by EX-CS), EX-IOExpander enables digital I/O expansion allowing many single or dual clip sound objects to be added to a layout.

Parts including relays, resistors, Dupont jumpers, wire, and a few speakers were selected because they were already “in-stock.”  I derive much enjoyment experimenting with electronics, others may not.  If you decide to move forward with DFPlayer clones, the best advice is.  Have Fun but Expect the Unexpected.

Finally, a special thanks to DCC-EX team members KC Smith and Chris Harlowe.  A few years ago, Chris’s help in creating momentary and latching route pushbuttons in EX-Rail and KC’s work with DFPlayer provided the foundation which this project is built on. 

Mark
From the Central Railroad of New Jersey
CNJ N Scale MOW and Farm Layout
250918 
DFPlayer USE Matrix

Three DFPlayer Operating Modes; Loop, Direct I/O and Serial Communications

 

Widely available positive level triggered opto-isolated relay boards designed to be driven by MCUs can simulate both short and long momentary button depressions or a latching switch.  Solid State Relays and sensors can also be employed.

Assuming the sound object requires only one or few different clips, operating the DFPlayer in either Direct I/O mode or Loop mode can be a viable alternative to Serial Communications mode.  There are instances where one or two clips Is all that is necessary for a given detail.  In Loop mode, a single audio clip playing the sound of burning wood in concert with the respective campfire lighting detail can suffice.  This allows allocation of the MCU’s serial ports for advanced sound objects that require many sound clips at a variety of volume levels.  

Order
The generally accepted file naming convention suggested is 0001xyz.mp3, 0002abc.mp3, 0003def.mp3 and so on.  While this is helpful in matching clips and how they are noted in code, technically the DFPlayer uses the order on which they were copied to the micro SD card.  It is the sequential entry into the disk’s FAT or File allocation table that determines the physical clip order.  Therefore, the first clip copied to the SD card is the first FAT entry, and so on.  Clips must be copied ONE at a time in sequential order.  The Windows Copy command DOES NOT copy clips in order if multiple files are selected and copied to the SD Card at the same time.  Some DFPlayer clones experience issues with clips less than 5sec.

File Naming and Order Example
Below shows the first 3 of the 26 Tower sound clips.  They were copied one by one to a micro SD Card.

 
Several mp3 clips on the Station’s DFPlayer micro SD Card
 
 
The DFPlayer
The DFPlayer is an inexpensive and simple device for incorporating sound objects or details on any model railroad.  Many incorporate it in serial communications mode with a Microcontroller (MCU), however the DFPlayer features two other operating modes that allow it to be added on traditional DC model layouts too!

The “Official” DFPlayer
       

DFRobot, DigiKey and other resellers offer the official DFPlayer.  A myriad of low cost DFPlayer clones are available from online retailers.  Be careful.  Many pictures do not show the actual MP3 decoder chip on the DFPlayer advertised.  There are multiple “models” sold.  Board silk screen printing shows either “DFPlayer Mini (some with HW247A next to it) or MP3 FN-M16P or MP3-TF-16P.  Photos of the first two DFPlayers purchased were manufactured with the MH2024K-24SS and the JL AB24CR9F35.1-74 mp3 decoder ICs.

     

Two ICs are found on the DFPlayer module board; a mp3 decoder chip and an 8002 class AB amplifier.  Class AB amplification is less efficient than the newer and more popular class D amplifier resulting in a relatively high idling or quiescent current.  Some clones suffer from an undesirable tone on power up.  The idling current drawn from the power supply for a DFPlayer is typically between 20-30mA.  The total supply current of approximately 45mA was measured during testing two concurrently idling DFPlayer modules, one of each of the two mp3 decoder types purchased.  The 8002 amp is rated at 3W @ 3 ohms, 2.65W @ 4 ohms and 1.8W @ 8 ohms.  The DFPlayer prefers Vcc at about 4.2V though 5V is more commonly used.  Supply voltage in excess of 5V can damage the DFPlayer.

Excluding the official DFRobot DFPlayer, there appears to be consensus that the YX5200 mp3 decoder chip is most compatible to the mp3 decoder on the DFRobot DFPlayer.  The MH-ETLive, GD3200D, TD5580A are other common clone mp3 decoder ICs.  There are many copies…

While the official DFRobot DFPlayer has not been tested, it should work without any problems.  It is usually best to buy a branded product rather than a knockoff when adopting a new device however since adding sound is not “mission critical” and there is about a 5 to 1 difference in cost, it was decided to first explore a couple of cheaper DFPlayer clones. 
Two versions, Two different mp3 decoders; 
the 24 pin MH2024K-24SS and the 			JL AB24CR9F35.1-74
     

Some of the differences and defects observed or reported elsewhere.  
MH2024K-24SS
Red operating light	Slide in SD Card	Hum on 3.3V None at 5V	Inconsistent library support.
JL AB24CR9F35.1-74
Blue Operating Light	Spring Card loader	Lower volume at max		Inconsistent I/O actions.

Two issues during testing for the planned use were discovered but acceptable solutions found.

MH2024K-24SS -- Does not play on cold boot (from power down) but does upon a warm boot (MCU reset button, via EX tools in Engine Driver or in the Arduino IDE serial monitor).  The current drawn from the 5V supply was slightly higher with this chip.  The fix - Swapped with the JL AB24CR9F35.1-74 version.  Trigger Port Pins I/O 1 and I/O 2 for Direct I/O mode, and ADKEY for Loop mode work on the MH2024K-24SS based DFPlayer.  

JL AB24CR9F35.1-74 – A short <1 second “squeal” sound upon cold boot.  A board modification of the similar MH-ETLive DFPlayer mp3 decoder addresses the issue however the board differences between it and the JL AB24CR9F35.1-74 requires additional re-work.  It was decided to delay any modification until either or both the YX5200 or official DFPlayer mp3 decoders are evaluated.  More testing will be performed regarding reported inconsistent reaction to I/O actions – I/O 1, I/O2 and ADKey1.  Sound checks from both JL AB24CR9F35.1.74 DFPlayers on the Dual Caddy were tested via I/O 1 and performs as defined.  Loop mode does not function however Direct I/O mode performs as defined.

Both Versions
Hum and motorboating noise present when an external stereo amplifier was connected to the DAC L and R audio outputs.  Amplified 2 channel or stereo is unneeded, however it was discovered that hum and motorboating marginally improved by free wiring the DFPlayer module instead of breadboarding it.  A significant reduction occurred when the 2nd ground, pin 10 of the DFPlayer was connected solely to the signal ground of the audio amplifier.  

One disadvantage adopting the DFPlayer is mounting.  There are no holes for fasteners and its double sided component layout coupled with pre-soldered pins significantly limits mounting options.  The inspiration for the creation of the caddy.  

Another DFPlayer disadvantage is micro SD card access.  Cards must be removed and inserted into a computer for adding, removing, or changing clips.
 
MP3 Sound Files – Creation and Ordering
Perhaps the most time consuming task is developing and organizing sound clips.   Three open-source programs, VOVSOFT’s Text to MP3 converter, VLC and Audacity played important parts in creating the sound clips.  Be cognizant of copywrite laws and regulations.

The Tower and Station human communications were written in a text editor or MS Word.  The text was copied into the Text to MP3 converter and saved as a mp3.  The mp3 was then imported into Audacity for clip modification such as adding reverb, adjusting volume in addition to any other desired effects and lastly, exported as an mp3.

 

Audacity is a fun program.  One can easily spend a lot of time adding a variety of effects.  The graphic equalizer can be very helpful in compensating for speaker deficiencies.  There are only several essential steps.  Eg Adding reverb.  Import mp3 into Audacity, Select Entire Clip, Go to Effect, Select Delay and Reverb, Reverb, Apply, Test via the Play button and if satisfied, Export to MP3.  Long clips can be shortened if needed.

 

VLC can extract audio content from a mp4 video and create an mp3 sound clip.  Sound clip modification, such as reverb, is subsequently performed in Audacity.  The convert screen ready to extract the audio track

 
Note about Volume…  A clip can sound loud during testing but too low when a couple of sound locomotives are running on the layout.  Plan on a few volume adjustments. 
The DFPlayer Dual Caddy for All

Caddy Wiring Schematic

LOOP Mode.
The schematic below depicts the MCU option for operating the DFPlayer in Loop Mode.  For traditional DC layouts, the relay NO and COM pins 1 and 2 are simply replaced with a SPST latching switch to turn on player.  The DFPlayer ADKEY1 pin 12 is permanently connected to DFPlayer ground which instructs the DFPlayer to function in Loop mode and play the clip on powerup.  No other mode can be used when ADKEY1 is at ground.

 

Direct I/O Mode.
While the wiring schematic illustrates connection for MCU driven layouts, sound clips are selected, Previous or Next, when either I/O 1 or I/O 2 respectively, is momentarily connected to ground by a relay or normally open momentary switches.
A longer momentary depression on I/O 1 decreases volume. Volume can be increased when I/O 2 is subject to a longer depression.  Swap the relay with a push button connected between I/O 1 pin 9 and ground and another pushbutton between I/O 2 and ground to operate the DFPlayer without a microcontroller.  

 
 
The DFPlayer Dual Caddy for ALL.  

Development

Bottom Interconnect Wiring
Breakable male and female headers were selected for their adaptability to mount different components and minimize parts. Extra space between the SD card and layout bottom side, compared to an IC socket, facilitates SD card swaps.

Separate Voltage In connections incorporating 2 pole screw terminals allow flexibility for powering each DFPlayer.  
Loop Mode Jumper wiring indicated in blue.
I/O Trigger Port 1, (YEL) and I/O Trigger Port 2 (GRN) are wired to separate single male Dupont header pins.

Caddy Bottom Interconnect Side
 

Caddy Layout and Connections
It is HIGHLY recommended to check for shorts, opens and continuity on new builds prior to IC insertion and applying power.
 

Power-Speaker-Triggering Ports and ADKEY1.  
The DFPlayer Dual Caddy features an independent power option for each DFPlayer.  
Speakers DF1 Speaker and DF2 speaker. Output connections from each DFPlayer to respective speaker. The DFPlayer’s single channel audio power IC, the 8002, is rated at 3W @ 3 ohms, 2.65W @ 4 ohms and 1.8W @ 8 ohms.
Loop Mode Jumper Blocks and Direct I/O Mode)
A jumper block for operating the player in Loop Mode.  The ground side can be used for MCU or relay ground.  Triggering Port pins I/O 1 and I/O 2 accessible from individual header pins.  
 
Construction Photos
After gathering the parts, spent a little time positioning several times before the outcome.  Component arrangement selected to minimize perf board area and minimize lengths of the interconnections.  

Assembly was straightforward and perhaps the most difficult aspect was maintaining flush top side component mounting when soldering the interconnections while the Caddy is bottom side up.  A very light coat of Elmer’s Glue All on the bottom of the pieces provided sufficient support until the parts were soldered.  

Glued Parts – Pre-Solder					Completed Caddy Interconnect
  	 
Checking For Continuity, Shorts and Opens				Ready for Testing
     
Direct I/O Mode Testing
 
 
The DFPlayer Dual Caddy (MCU)

Caddy Wiring Schematic
The Dual DFPlayer Caddy for MCU schematic or half of it is essentially the same circuit as shown on the DCC-EX website with a few exceptions and convenience features.  Two DFPlayers, RX/TX resistor bypass, separate power supply inputs and taps plus I/O 1 access for the most part, differentiates the two. 

 
The current drawn by a single DFPlayer module at maximum volume can easily exceed 200mA.  Add a separate power supply when using DFPlayers.  A ground connection between the MCU and the DFPlayer is required when powering the DFPlayer by a separate power supply and operated in Serial Communications mode.  Direct I/O and Loop modes require a ground connection between the MCU and the relay’s ground.

Other simple enhancements include Multi-Voltage MCU Support that inserts or bypasses the 1k ohm resistors in series with the RX/TX inputs of the DFPlayer depending on whether a 5V or 3.3V MCU is controlling the DFPlayer.  Access to the DFPlayer I/O 1Trigger Port, Pin 9, is accessible via a male Dupont Pin.  It is good for testing the DFPlayer output.  I/O 1 can play the Previous clip (or first clip) and decrease volume from the default maximum.   The 1k ohm resistor is optional.

Caddy Development
A DFPlayer Dual Caddy seemed to make most sense, not just economically, but a WiFi equipped Arduino Mega leaves only 2 available serial RX/TX ports, without I2C expansion, for adding serial controlled devices e.g. DFPlayer.  

Breakable male and female headers were selected for their adaptability to mount different components and minimize parts. Extra space between the SD card and layout bottom side, compared to an IC socket, facilitates SD card swaps.

Separate Power In connections allow flexibility for powering each DFPlayer.  A 2-pole screw terminal along with 4 male Dupont terminals can be implemented in several ways such as daisy chaining power or access to ground.  

Caddy Bottom Interconnect Side
  
Caddy Layout and Connections

 

Power-Speakers-RX/TX
Power   DF1 - + P/S and DF2 – and +
The dual DFPlayer board features an independent power option for each DFPlayer.  Power supply taps are provided for bridging a single power supply connection from either DF power input to the other.  The separate power inputs enable additional options.  Some clone DFPlayers may function better when power is fed to each separately.

Speakers   DF1 Speaker and DF2 speaker.
Output connections from each DFPlayer to respective speaker.  The DFPlayer’s single channel audio power IC, the 8002, is rated at 3W @ 3 ohms, 2.65W @ 4 ohms and 1.8W @ 8 ohms.

Communication Ports   DF1 R/X and DF2 RX/TX
Screw terminal blocks provide connection from the RX/TX pins of the module.  1k ohm resistors are in series with both RX/TX lines to protect the DFPlayer from excess voltage from 5V MCUs such as the Arduino Mega.  Some reported that a few of the DFPlayer clones function only when both RX/TX lines include a 1k ohm series resistor.

ByPass Jumper Blocks and I/O Pin Access (Testing + Direct I/O Mode)
DF 3.3V MCU RX/TX By-Pass Jumper Blocks
Lower operating voltage MCUs, such as the Nucleo, function at safe voltage levels for the DFPlayer eliminating the need for the 1k ohm RX/TX level protection resistors.

I/O Pin Access   DF1 I/O 1 and DF2 I/O 2
The triggering port pin I/O 1 can be used as a basic diagnostic tool.  A momentary contact to ground instructs the DF player to play the previous mp3 at the default volume.  If there is only one mp3 saved on the SD card, it would be played.  A longer momentary contact will decrease volume.  The I/O control pin overrides whatever the DFPlayer was doing previously.  The ability to play a sound in this manner allows one to test basic functionality and isolate if an issue exists.  Typically, if the DFPlayer produces sound when I/O 1 is momentarily grounded, then most likely the problem is either in RX/TX, grounding-MCU, code etc.  A momentary push button connected between I/O 1 and ground does a fine job for both short and long depressions too.   
Construction Photos
After gathering the parts, spent a little time positioning several times before the outcome.  Component arrangement selected to minimize perf board area and minimize lengths of the interconnections.  However, the board is slightly larger than necessary to allow for adding future options such as male Dupont header pins for I/O 2, ADKEY1 or other unassigned DFPlayer function pins. 

As with the DFPlayer Dual Caddy for ALL, assembly was straightforward and perhaps the most difficult aspect was maintaining flush top side component mounting when soldering the interconnections.  A very light coat of Elmer’s Glue All on the bottom of the pieces provided sufficient support until parts were soldered.  

1-Glued Parts – Pre-Solder		2-Completed Caddy Interconnect	
      

3-Checking For Continuity, Shorts and Opens		4-Ready for Testing
    

5-Layout Installation Preparation 			6-Final Testing
     

 
DFPlayer Serial Communication Mode 
DCC-EX EX-Command Station aka EX-CS combined with EX-Rail is a powerful way to control the DFPlayer.  The EX-Rail programming illustrated in the following examples are intended for demonstrating DFPlayer.  It is highly suggested to review the related DCC-EX documentation for further details.  Disclaimer: The author lacks programming skills.

HAL Hardware Abstraction Layer Coding.
There are two methods for defining DFPlayer hardware that enable usage in EX-CS; the myHal.cpp file and the new way, in myAutomation.h file.  

myAutomation.h						myHal.cpp
HAL(DFPlayer, 1000, 16, Serial2)			#include "IODevice.h"
HAL(DFPlayer, 1100, 15, Serial3)			#include "IO_DFPlayer.h"
							void halSetup() {
  DFPlayer::create(1000, 16, Serial2);
  DFPlayer::create(1100, 15, Serial3);
}
The first, second, and third Engine Driver aka ED screenshots represent the Tower and Station sounds.  The 4th screen, Lighting, shows the campfire.  Besides manual control via ED, the tower “speaks” whenever a turnout state changes or a locomotive automation begins or ends.  Adding sensors or EX-FastClock to trigger sounds is an alternative to route buttons.  
  
Coding Examples –In either the parent myAutomation.h file or a child, e.g. the mySounds.h file.

PLAYSOUND = ANOUT = SET
Important- Without additional coding, if a clip is being played and the DFPlayer is instructed to play another, the first clip stops and the new clip begins.  The WAITFOR(abcd) or AT(-abcd) where abcd is the port assigned to the DFPlayer, tells the DFPlayer to finish the playing the current clip before proceeding to play the next.

It would be helpful if EX-Rail supported the TBD 3rd parameter and defined it as a Flag in PLAYSOUND and/or ANOUT; 
---None(default)	If instructed to play a clip while currently playing one, the clip playing aborts and the new clip begins.
---a		Argument to direct the DFPlayer to finish playing the current clip before proceeding (Instead of a separate command)
---b		Argument to tell DFPlayer if interrupted, return to the clip after playing the 2nd clip.(No equivalent to date)
According to the specification sheet, the DFPlayer firmware includes an Advertising Sound Waiting Function ASW; 
“the music can be suspended when advertising is over in the music continue to play.  Hopefully a future EX-CS release will support Return.

Throttle Routes button – First Button Leftmost Screen
  
1000 (Tower DFPlayer) hardware port defined earlier for the DFPlayer, play the 25th clip at volume 25/30

A Routes button example for the Station shown on the 2nd screen.
  
1100 (Station DFPlayer) hardware port defined earlier.  Play the 3rd clip at volume 20/30 
The tower reports any change in turnout status.  Located in myTurnouts.h, 
 

Note: The MESSAGE command pushes a text message on every throttle connected to EX-CS 

When the layout is powered on, the Tower and then the Station, welcomes all.  Turnouts are set to their default positions.

 

Routes button example for Loop Mode “Tunnel Winds.”
After the left most screen shot was taken, a button was added for “Tunnel Winds.”  The howling Tunnel Winds clip is located on a SD card in a dedicated DFPlayer operated in Loop Mode with a speaker in the tunnel.  It was arbitrarily placed on the Tower screen.  The button functions as a latching switch.  

 
Whereas 39 is the Arduino Mega’s Digital I/O pin connected to a DFPlayer relay input. 200 is an available Latch.

Routes button example for Direct I/O Mode “Campfire - Winds.” (The rightmost Engine Driver screenshot)
The Campfire lighting detail is complimented by campfire sounds.  Or, it can play howling wind sounds.  (The Tower and Station DFPlayers can also play the howling wind clip).  Route buttons function as momentary switches.

 

Arduino Mega Digital I/O Pins 37 and 38 connect to separate relay inputs that momentarily place I/O 1 or I/O 2 at ground.  Two routes each for simulating short and long depressions.  Short Contact or Depression = 500 mS and Long Depression = 1000 mS or 1 S.  The volume number of steps were not counted but the range was more than sufficient. 
Parts List (Prices from AliExpress as of 250907
-- DFPlayers and micro SD cards (Up to 32GB) – DFPlayer Clones start from $1.50.  The Official DF MSRP $5.90

---2.54mm Breakable Headers Male and Female Single Row 40 Pin Pair 10 pack-$2.17 (Jumper Blocks from Females)
 
---KF128 2P 2.54mm Plug-In PCB screw terminal block connector 26-18 AWG -- $3.16  

---4 Piece Small Perf Boards Set -- $1.65 

---1k 1/8 W Carbon Film Resistors (MCU) and extras for wiring.  Buy an assortment for about $4 or a single pack of 1k ohm resistor for about $1.50.  Bottom board interconnecting wire is from rarely installed values of resistors.  Insulated bottom board wires are extra Dupont breadboard wires with ends cutoff.  M-M, F-F and M-F packs are around $1.50 each.

---5V 3A Buck Converter $2.99.  The Buck output USB connector was cut off to feed the power distribution strips.
    
--- Power Distribution Barrier Strip- $1.47 – Cut in half for 6P.  Make bridging wire for each 6P block.  
   

---Relay (2 or 4 Channel Positive/Negative Level Triggered OptoIsolated) $2.25-$6.30
(Both Loop and Direct I/O Req. Positive Level)
      

---Male and Female Dupont Wires.  About $1.50 per selection(M-M, M-F, F-F) 

---Speakers and Latching or Momentary Switches if No MCU.  The choice is yours.

