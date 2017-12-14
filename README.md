# 32bit Retro Gaming
The contents of this repo helps you avoid some frustrations when setting up a 32 bit AMD K7 Retro Gaming System

It turns out that its actually pretty hard to setup an old Duron pc for retro gaming! I hope to save you some frustrations by sharing the experiences I've had setting up my old pc.

## The Plan before hand
I wanted to go Multi-CPU Duron first. I got an old Tyan Server board from electromyne in Germany(via eBay) and tried to jump the MP-jumper on the old AMD Duron CPU to enable multi CPU support but I had no success. I decided to go back to my old setup I had back in the day, with the exception of using some extra memory and a more modern videocard to take away some bottlenecks I had when I moved to another system at that time. This is what I ended up with;

## The system I am Using vs what I had back around 2002-2005
- AMD Duron 1800
- Asus A7N8X Rev 1.06B -> I had a A7N8X-X which was AWESOME and EXTREMELY STABLE. This one tends to be unstable at times.
- SiS-180 SATA Raid PCI card -> I made the wrong assumption that the A7N8X had sata just like the A7N8X-X that I had. Bummer but hey.. at least it was cheap. There are no Text based drivers available for this card which only makes it usable for something like a secondary sata hdd preloaded with games.
- 3GB DDR1 PC3200 -> I had 1.5GB Single Channel.
- Asus HD3850 -> I had a Geforce FX5200




## Lessons Learned getting the system to work

### AMD Duron is not being recognized by A7N8X
The A7N8X board made the AMD Duron show up as Unknown CPU Type when using BIOS version C1003. The motherboard originally came with BIOS version C1002, but was upgraded to C1003 by its previous owner. BIOS Version C1008 will make the BIOS recognize the Duron CPU.

### Flashing the Award BIOS with the awdflash from the original Bios resulted in a bricked system
After downloading Bios Version C1009, Creating a DOS Boot Floppy in XP and copying the BIOS BIN file to that same floppy, I actually managed to brick my BIOS when i used the awdflash that is bootstrapped into the bios (Extracted to floppy? after holding ALT+F2 after POST). It managed to erase the BIOS and said:
" Bios is write-protected ".
not flashing anything and resulting in a bricked system.
I managed to solve this by using/adjusting info from an old forum thread here: http://www.overclockers.com/forums/showthread.php/299322-A7N8X-BIOS-Recovery
! I have tried 20 versions of awdflash tools before I got mine to work. I experienced everything from a non-booting floppy to the flash not starting. !
Below is the setup that worked for me;

#### Set up a Floppy to fix and update the BIOS after Bricking it ( Instructions are for a A7N8X rev 1.06B , Update to C1008 )
--- USE AT YOUR OWN RISK ---
1. Create a standard DOS Boot floppy via Windows (On a working computer)
2. Copy the Boot Block BIOS loader utility to bypass the award boot block. This will make your pc boot to DOS from the Floppy and enable you to run your own version of AWDFlash. (The block utility is called awdblock.zip on this repo)
3. Add the Award Flash utility to the floppy (I downloaded 8.59E from the a site called wimsbios; https://www.wimsbios.com/awardflasher.jsp) and renamed the AWDFLASH executable to FLASH.EXE.
(Note: The flash utility will differ in command line usage across versions, so be sure to check the expected/required parameters by running the flashtool in a commandprompt in windows with parameter /help to see the available parameters.)
4. Copy the bios file (example AN8B1008.BIN) to the Floppy
5. Open Notepad and type the following; (DO NOT -> EDIT<- THE EXISTING AUTEXEC.BAT ON THE FLOPPY, BUT CREATE A NEW FILE IN NOTEPAD AND THEN LET NOTEPAD OVERWRITE THE ONE THATS ON THERE.)

@ECHO OFF
FLASH AN8B1008.BIN /py/sn/Sb/LD/cd/cc/cp/R

6. Boot your PC; It should erase and flash the BIOS.

## Drivers for Asus A7N8X - Hacking Asus Support Site URL to spawn the driver page you need.
It turns out it was pretty hard to get the drivers for the A7N8X!
When you search for it on the Asus Support site it won't turn up with any results, but when you search on google it will come up with something like;
https://www.asus.com/supportonly/A7N8X-E%20Deluxe/HelpDesk_Download/
Which is nice, but not the variant of the board I'm using.

Some URL hacking later, and we have ourselfes a driver page!
https://www.asus.com/supportonly/A7N8X/

This repo has the drivers I managed to download for archiving purposes.

## Getting a Browser for a K7 AMD Duron CPU ( Chrome vor non-SSE2 CPU s )
Chrome 34.0.1847.137 is the last Chrome version to support non-SSE2 CPUs

