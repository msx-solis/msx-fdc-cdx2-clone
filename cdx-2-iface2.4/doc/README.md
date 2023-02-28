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




![CDX-2](/cdx-2-iface2.4/pictures/IMG_20230217_1639012.jpg )

### Look at YouTube:
[![YouTube link](https://img.youtube.com/vi/UTZCwYuuAXE/0.jpg)](https://www.youtube.com/watch?v=UTZCwYuuAXE)
