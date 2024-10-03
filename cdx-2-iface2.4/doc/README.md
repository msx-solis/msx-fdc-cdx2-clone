# Step by step debugging instructions
## Port Based Floppy Disk Drive controller for MSX computer



Recreated Microsol Tecnologia CDX-2 FDD interface with busdir signal upgrade.

### ROMs tested with this interface:

* CDX-2 (Microsol Tecnologia)
* Angeisa (Angeisa Eletronica LTDA)
* FAST!DiskROM

### ROMs that should work with this interface:

* DDX 1.0 (Digital Design)
* DMX 1.2 (Conector Informatica LTDA.)
* LIFTROM (Liftrom Informatica)
* MANUT (AMT Mamute)
* TPX 1.02 (TPX - Perifericos)

### ROM vs free BASIC memory

| ROM | Free BASIC Memory |
| ------------- |:-------------:|
| Angeisa (Angeisa Eletronica LTDA)  | 23430  |
| CDX-2 (Microsol Tecnologia)  | 23430  |
| DDX 1.0 (Digital Design)  | 20304  |
| DMX 1.2 (Conector Informatica LTDA.) | 20304  |
| LIFTROM (Liftrom Informatica)  | 20304  |
| MANUT (AMT Mamute)  | 23430  |
| TPX 1.02 (TPX - Perifericos)  | 23430  |
| FAST!DiskROM  | 25471  |

Solder in all components and sockets, using round pin sockets you should have a low profile design.
The Jumpers JP1 to JP4 should link 1-2 for standard MSX connection and 2-3 for to use a standard PC ribbon cable, but drive b: may not work in this case (test not done yet). JP5 selects the ROM software between two options.

Then follow the next testing steps.

First insert the 74LS04 and verify you have 4Mhz measuring here (you need a frequency-meter or an oscilloscope):
![4Mhz](/cdx-2-iface2.4/pictures/IMG_20230218_1133025.jpg)
Same way you can insert the 74LS74 IC and test you have 1Mhz here:
![1Mhz](/cdx-2-iface2.4/pictures/IMG_20230218_1330519.jpg)
Then test the reading select circuit is working properly doing the test shown in the following picture (and testing the result with a logic probe or a voltmeter):
![read](/cdx-2-iface2.4/pictures/IMG_20230218_1654045.jpg)
You can use the same program (push ctrl-stop and RUN) for test writing port select circuit too (with the probe pin inserted at pin 2).
Click at the below picture to see a video showing it:
[![YouTube link](https://github.com/msx-solis/msx-fdc-cdx2-clone/raw/main/cdx-2-iface2.4/pictures/IMG_20230218_1652428.jpg)](https://youtu.be/hXyXDxHcx18)
After that you can also probe the hex D4 port with the following procedure:
![D4](/cdx-2-iface2.4/pictures/IMG_20230218_1746467.jpg)
Now you must configure the jumpers JP1 to JP4 for the right drive and the right wire:

* To use an old DS0 MSX drive, build a direct straight ribbon cable and choose 1-2 at four jumpers. Direct straight drive connected will be A: and switching wires 10-12 drive B: DS0 (MSX) can be connected.
* To use a common DS1 PC drive and a ribbon PC twisted cable (with 10 to 16 wires crossed) chose 2-3 at those jumpers (only drive A will work).
* PC drives can also be used with an MSX setup, with a 10 to 12 ribbon twisted wire. For this setup move jumpers JP1-JP4 to 1-2 and connect two PC drives: direct straight will be drive B: and drive connected after switching 10-12 will be drive A:.
* Some drives also lets you choose what DS setup they are by jumpers, then use a direct straight ribbon cable with up to 5 connectors (4 drives) and setup each drive from DS0 to DS3.

Now try the following output commands (to test DS0 ON, DS1 ON, motor ON...) and test on the related pins. to know what should be the affected pin you must follow the schematic...
![binary1](/cdx-2-iface2.4/pictures/IMG_20230218_1757110.jpg)
...or you can connect now the floppy drive and test it. &b00100001 should on the A drive led, there's also bits for motor, etc:
 ![binary2](/cdx-2-iface2.4/pictures/IMG_20230218_1803597.jpg)
Then, insert all pending IC and configure the JP5 to select your favorite ROM driver and try with a disk drive.
Angesia ROM would be the better software to use during the test process and FAST!DiskROM could be better option to improve the disk performance.

Floppy disk support must be formatted at the right format, MSX system does not support High density disks.
This means 3.5 HD disks must be formated after bloking the HD hole, using 720k/360k format (DSDD 80/40 tracks), and 5.25" disks must be also setup for 360k.
You can use a tool from a PC to dump MSX disks, is called Disk Manager: http://www.lexlechz.at/en/software/DiskMgr.html
Then you can use the disk dumps fount at https://download.file-hunter.com/ and get access to lots of software/games.

There's also lots of information for troubleshooting this interface reading the TMS2793 datasheet.
https://github.com/msx-solis/msx-fdc-cdx2-clone/raw/main/cdx-2-iface2.4/doc/tms2793.pdf
