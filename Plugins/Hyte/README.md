# HYTE CNVS Protocol Document V1.0 

2023/06/30 

1\. PID & VID 

| Hardware Version  | VID  | PID |
| ----- | ----- | ----- |
| 1  | 3402  | 0B00 |
| 2  | 3402  | 0B01 |

We are using USB serial port. 

2\. Get the firmware version. 

| Write |  |  |  |  |  |  |
| :---- | :---- | ----- | :---- | :---- | :---- | :---- |
| FF  | DD  | 02 |  |  |  |  |
| Read  |  |  | Large  | Mid  | Small software Version update  | Hardware Version |
| FF  | DD  |  | 02 0-255  | 0-255  | 0-255  | 0-255 |

3\. Turn on/off firmware animation (when firmware animation is off, you can start software  streaming) 

| FF  | DC  |  | 05 on/off |
| :---- | :---- | :---- | :---: |
|  |  |  | 0: off |
|  |  |  | 1: on |

4\. Turn on/off startup animation (our CNVS shows a default startup animation each time  CNVS is plugged in, but user can choose to turn it off) 

5\. Turn on/off when pc is off (CNVS can keep lighting up when PC is off, but user can also  choose to turn it off when PC is off) 

|  |  |  | On/off startup animation  | On/off when PC is off |
| :---- | :---- | :---- | :---- | :---- |
| FF  | DC  |  | 07 00: on  | 00 : off |
|  |  |  | 01: off  | 01 : on |

6\. Get turn on/off startup animation and turn on/off lighting when PC is off setting from  firmware.

| Write |  |  |  |  |  |  |  |  |
| ----- | :---- | ----- | :---- | :---- | ----- | ----- | ----- | ----- |
| FF  | DC  | 08 |  |  |  |  |  |  |
| Read (9 byte) |  |  |  |  |  |  |  |  |
|  |  |  | On/off startup animation  | On/off when PC is off |  |  |  |  |
| FF  | DC  |  | 08 00: on  | 00 : off  | 0  | 0  | 0  | 0 |

The HYTE CNVS Protocol is provided under the terms of the GNU General Public License version 2\. 

|  |  |  | 01: off  | 01 : on |  |  |  |  |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |

7\. Streaming command (our CNVS contains 50 LEDs) 

|  |  |  |  | Led Count |  |  |
| :---- | :---- | ----- | ----- | ----- | ----- | ----- |
| Byte0  | Byte1  | Byte2  | Byte3  | Byte4  | Byte5  | Byte6 |
| FF  | EE  | 02  | 01  | 00  | 0x32  | 00 |

(From byte 7 to byte 156 is the RGB byte for Led1 to Led50) 

| Byte7  | Byte8  | Byte9  | Byte10  | Byte11  | Byte12  | …  | Byte154  | Byte155  | Byte156 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| R1  | G1  | B1  | R2  | G2  | B2  | …  | R50  | G50  | B50 |

CNVS LED layout.

<img width="621" height="163" alt="image" src="https://github.com/user-attachments/assets/adf0c0c8-0925-4597-9f21-5f5cbd57f1b4" />


The HYTE CNVS Protocol is provided under the terms of the GNU General Public License version 2\. 



