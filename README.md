260625 DCC-EX 5.6.0 DFPlayer Compatibility Update

DFPlayer Modules with TD5580, JC AB24CR9F35.1-74 or MH2024K-24SS mp3 decoders were evaluated and function under DCC-EX 5.60.  Testing was performed on an Elegoo Mega employing Serial ports 2 and 3 and powered by 9VDC.  A separate 5VDC PS supplies voltage to the Dual DFPlayer Caddy DFPlayer.  No caddy or schematic changes were needed and are the same as shown in the original video and documentation

Corrected by the following actions;
1-Removed the “#include "IO_DFPlayer.h” statement and deleted the number of tracks allocated in HAL statement section from myAutomation.h 
	
Example:  From HAL(DFPLAYER, 1000, 40, Serial2) 	to HAL(DFPLAYER, 1000, Serial2)

2-Renamed the mp3 files eliminating one preceding zero in file name prefix.
Example: From    0001-WelMan.mp3 		to    001-WelMan.mp3
Prior DCC-EX releases from 5.4.10 to 5.4.19 work with either form

***As with all versions--Fast Format(FAT32) uSD before copying mp3 files.  If it’s a new uSD, then Full Format (FAT32)

3-Created a directory “01”on uSD
	mp3s played from root directory in prior DCC-EX releases from 5.4.10 to 5.4.19

4-Copy mp3 files into the “01” directory on the uSD in sequence one at a time

Solved 95%.  Excluding issue with Tower Turnout (TO) announcements only occurring at startup.

5-The configuration file myAutomation.h defines the default TO positions at powerup or reboot.  When AUTOSTART in the myAutomation configuration file is executed, a 9sec delay was inserted between each TO command to prevent all TOs from being closed or thrown at “essentially” the same time.  The delay of 9sec, which worked in prior releases, caused TO2 and TO4 announcements to abruptly terminate however announcements for TO1 and TO3 completely played in DCC-EX 5.6.0.   The delays allow sufficient time for recovery.  Changing the 9sec delay to 8 secs corrected the problem.  Not being a coder, perhaps another method could have resolved this issue.

IMPORTANT-Remember-
--All instances of PLAYSOUND in EX-Rail scripts must be revised to PLAY_TRACK and the 3rd argument deleted)
As an example…  In the myToSounds.h 
The PLAYSOUND(1000,1,18,0) is changed to PLAY_TRACK(1000,1,18)



ORIGINAL ReadMe
A repository for documenting the implementation progress of the DFPlayer.
Two variations depending on application.

A converted PowerPoint presentation to mp4 video will be posted on YouTube which includes video clips of various points in the development of the caddies.

Most of the “slides” have a significant amount of content and some far more than what can be read in the time allotted per slide though should be sufficient to convey the process.  



