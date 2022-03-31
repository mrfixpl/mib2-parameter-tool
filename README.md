# mib2-parameter-tool
Rear, analize, customize VAG MIB2 parameters

## Purpose ##
Backup parametrization from MIB2 main unit (module 0x5F), analize it, modify it, upload back to unit. Without VCP.

## Functions (planned) ##
* Sound parameters upload
* Additional sound equilizers activation
* Subwoofer controls
* Video in motion / MirrorLink in motion activation
* In-Car Communication (ICC) activation

## Research ##
### Intro ###
* Parameters are store in EEPROM.
* Complete parameter in unit is made out of datasets.
* Each dataset contains infromation about how certain function of the unit should work.
* Each dataset is stored at certain address in the unit memory.
* Dataset address can be different for `STD` and `HIGH` units, also can change with firmware versions.
* Last two bytes in dataset is checksum CRC-16/CCITT-FALSE

### Datasets ###
* DTCP
* ASAM ODX MUX
* hmi control speed (`0x240`)
* langauge
* visible mmi language
* powermanagement timer
* audio parameter sound (`0x3000`)
* dab frequency
* audio parameter sound announcement (`0x3600`)
* audio manager mute hmi constant
* audio parameter telephone
* audio parameter SDS
* audio parameter individual sound processing
* eco HMI
* audio parameter sound cabrio
* audio parameter sound configuration (`0x3B00`)
* speach signal enhancement
* in car communication (`0x7000`)
* air quality

## Reference ##
https://www.drive2.ru/l/611261670785849626/
https://www.drive2.ru/l/574649307970404656/
https://crccalc.com
