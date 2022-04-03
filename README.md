# MIB2 Parameter Tool
Read, analize, customize, generate VAG MIB2 parameters

## Purpose ##
Backup parametrization from MIB2 main unit (module 0x5F), analize it, modify it, upload back to unit. Without VCP.

## Functions (planned) ##
* Parametrization data read/backup
* Analize data
* Additional sound equilizers activation
* Subwoofer controls
* Video in motion / MirrorLink in motion activation
* In-Car Communication (ICC) activation
* Parametrization restore/upload

## Usage ##
placeholder

## Research ##
### Intro ###
* Parameters are store in EEPROM.
* Complete parameter in unit is made out of datasets.
* Each dataset contains infromation about how certain function of the unit should work.
* Each dataset is stored at certain address in the unit memory.
* Dataset address can be different for `STD` and `HIGH` units, also can change with firmware versions.
* Last two bytes in dataset is checksum CRC-16/CCITT-FALSE
* Since MIB2 units have build-in audio amblifier with 6 output channels, it's possible to use all 6 with correct dataset. From factory Audi Sound System (Audi A3 8V) and Seat Sound System (Seat Leon MK3 5F) are using 6 channels for 9.1 system (`9VD` package with 4x2 speakers in doors, 1x center in dash, 1x subwoofer in trunk, without external amplifier). It should be possible to add subwoofer in other cars (VW Golf MK7 5G, Skoda Octavia MK3 5E), wire it to MIB2 main unit, and enable sound output.
* It looks like `0x003B00` is empty in MST2 Technisat unit and there's a bin file in the J5 instead: `/tsd/etc/audio/soundcurves/configuration.bin`. Uploading custom dataset to `0x003B00` does not show any change in system.

### Datasets ###
* DTCP
* `0x200` - ASAM ODX MUX
* `0x240` - hmi control speed
* `0x280` - langauge
* `0x2D0` - 0visible mmi language
* `0x440` - powermanagement timer
* `0x460` - DAB frequency
* `0xDA0` - audio manager mute hmi constant
* `0x700` or `0x7100` - audio parameter individual sound processing
* `0x2F00` - eco HMI
* `0x3000` - audio parameter sound
* `0x3600` - audio parameter sound announcement
* `0x3B00` - audio parameter sound configuration
* `0x3F00` - audio parameter telephone
* audio parameter SDS
* audio parameter sound cabrio
* `0x4500` - speach signal enhancement
* `0x7000` - in car communication
* air quality

## Reference & Sources ##
* https://www.drive2.ru/l/611261670785849626/
* https://www.drive2.ru/l/574649307970404656/
* https://github.com/NumberOneBot/mqb-mib2-sound-datasets
* https://crccalc.com
* https://stackoverflow.com/questions/30035582/how-to-calculate-crc16-ccitt-in-php-hex
