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

Build all components using sockets, round pin sockets should have low profile on this design.
Then follow the next steps.
First verify you have 4Mhz measuring here (you need a frequency-meter or an oscilloscope):
![4Mhz](/cdx-2-iface2.4/pictures/IMG_20230218_1133025.jpg)
Same way check you have 1Mhz here:
![1Mhz](/cdx-2-iface2.4/pictures/IMG_20230218_1330519.jpg)
Test the read port is correct doing like in the following picture (you need a digital test probe):
![read](/cdx-2-iface2.4/pictures/IMG_20230218_1654045.jpg)
The same program with ctrl-breack and RUN can be used for writing test (with the probe pin at pin 2).
After that you can probe the hex D4 port that way:
![D4](/cdx-2-iface2.4/pictures/IMG_20230218_1746467.jpg)
Then test output commands (DS0 on, DS1, motor on...) check the schematic to know what are the right bits:
![binary1](/cdx-2-iface2.4/pictures/IMG_20230218_1757110.jpg)
or...
 ![binary2](/cdx-2-iface2.4/pictures/IMG_20230218_1757378.jpg)
Then, insert all pending chips, verify the D4 signals go to the pin they are expected and try with a disk drive.
Angesia ROM will be better driver to load for testing and FAST!DiskROM for better performance.

There's more information on the TMS2793 datasheet.












![CDX-2](/cdx-2-iface2.4/pictures/IMG_20230217_1639012.jpg )

### Look at YouTube:
[![YouTube link](https://img.youtube.com/vi/UTZCwYuuAXE/0.jpg)](https://www.youtube.com/watch?v=UTZCwYuuAXE)
