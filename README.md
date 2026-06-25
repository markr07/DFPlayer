6/25/2026 DFPlayer Update.
The DFPlayers’ equipped with the TD5580, JC AB24CR9F35.1-74 and MH2024K-24SS decoders have been tested and function under DCC-EX 5.60.  Testing performed on Elegoo Mega Serial 2 and 3 with 9V PS on Mega and 5V Dual DFPlayer as shown in the original video and documentation

Issues corrected by the following
1-Eliminating the reference to the number of tracks allocated in HAL statement
“HAL(DFPLAYER, 1000, 40, Serial2) to HAL(DFPLAYER, Serial2)
--Fast Format SD (always do whenever re-copying mp3 files)

2-Renaming mp3 files to eliminating one preceding zero in file name prefix
--Fast Format SD

3-Created a directory “01”on uSD.

4-Copy mp3 files to “01” on uSD

Solved 95%.  Excluding issue with TO messaging specifically occurring at startup.

5-Announcements for TO2 and TO4 stopped playing b4 finishing.  At startup, a delay is inserted to prevent all TOs from being set to default state at powerup and to close or throw sequentially with 9secs in between each.  The previous delay of 9sec caused TO2 and TO4 announcements to abruptly terminate but announcements for TO1 and TO3 were AOK.  Changing the 9sec delay to 8 secs corrected the problem. 

IMPORTANT-
Remember-
All instances of PLAYSOUND in EX-Rail scripts must be revised to PLAY_TRACK and the 3rd argument deleted)
As an example…  In the myToSounds.h 
The PLAYSOUND(1000,1,18,0) is changed to PLAY_TRACK(1000,1,18)


ORIGINAL ReadMe
A repository for documenting the implementation progress of the DFPlayer.
Two variations depending on application.

A converted PowerPoint presentation to mp4 video will be posted on YouTube which includes video clips of various points in the development of the caddies.

Most of the “slides” have a significant amount of content and some far more than what can be read in the time allotted per slide though should be sufficient to convey the process.  



