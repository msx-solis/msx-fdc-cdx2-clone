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

Then follow the next testing steps.

First insert the 74LS0 and verify you have 4Mhz measuring here (you need a frequency-meter or an oscilloscope):
![4Mhz](/cdx-2-iface2.4/pictures/IMG_20230218_1133025.jpg)
Same way you can insert the 74LS74 IC and test you have 1Mhz here:
![1Mhz](/cdx-2-iface2.4/pictures/IMG_20230218_1330519.jpg)
Then test the reading select circuit is working properly doing the test shown in the following picture (and testing the result with a logic probe or a voltmeter):
![read](/cdx-2-iface2.4/pictures/IMG_20230218_1654045.jpg)
You can use the same program (push ctrl-stop and RUN) for test writing port select circuit too (with the probe pin inserted at pin 2).
Look at this video:
[![YouTube link](https://github.com/msx-solis/msx-fdc-cdx2-clone/raw/main/cdx-2-iface2.4/pictures/IMG_20230218_1652428.jpg)](https://youtu.be/hXyXDxHcx18)
After that you can also probe the hex D4 port that way:
![D4](/cdx-2-iface2.4/pictures/IMG_20230218_1746467.jpg)
Now you must configure the jumpers JP1 to JP4 for the right drive&wire

### *To use MSX DS0 FDD and flat ribbon cable choose 1-2.
### *To use PC DS1 FDD and PC twisted (10 to 16 wires) select 2-3 at those jumpers.
### *PC drives can also be used with an MSX setup and 10 to 12 twisted wire.

Then test output commands (DS0 on, DS1, motor on...) check the schematic to know what are the right bits:
![binary1](/cdx-2-iface2.4/pictures/IMG_20230218_1757110.jpg)
or you can connect the floppy drive and test it.
 ![binary2](/cdx-2-iface2.4/pictures/IMG_20230218_1803597.jpg)
Then, insert all pending chips, verify the D4 signals go to the pin they are expected and try with a disk drive.
Angesia ROM would be the better driver to load when testing and FAST!DiskROM will be used for better performance.

There's more information on the TMS2793 datasheet.
https://github.com/msx-solis/msx-fdc-cdx2-clone/raw/main/cdx-2-iface2.4/doc/tms2793.pdf
