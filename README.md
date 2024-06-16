
# RAMbow - 1Mbyte memory expansion for Rainbow 100
"RAMbow flexes memory muscle" was the headline of a hardware review in the Silicon Valley Rainbow bulletin in October 1987.<br>
The article, which you can read in full [here](https://github.com/na103/rambow/blob/main/docs/RAMbow.pdf), discusses a memory expansion designed by Jerry Miller and marketed by Suitable Solution.<br>
This expansion could extend the memory of the first version of the Rainbow 100 (revision A) beyond its design limit of 256KB.<br><br>
![alt text](https://github.com/na103/rambow/blob/main/img/rambow.jpg "RAMbow")
<br>
The Rainbow 100 initially came with only 64KB onboard, which could be expanded via the option RAM up to a maximum of 256KB.<br>
Later, DEC developed an 8087 adapter card that allowed the option RAM card of the Rainbow 100 B to be used in rev A, enabling memory expansion up to a maximum of 832KB with a sandwich installation.<br>
RAMbow combines the 8087 adapter and the option RAM of the Rainbow B into a single card, allowing 896KB of memory on the 100A.<br>
Inspired by this article, I modified [my remake of the option RAM rev. B](https://github.com/na103/rainbow100-memory) with a single 1MB DRAM bank, creating room to accommodate the 8088 CPU socket.<br>
Indeed the main problem with the 100A is that the expansion connector of the option RAM lacks the A16 to A19 address lines, necessitating the relocation of the CPU onto the memory card.<br>   
In this repository you will find all the information needed to build my interpretation of the legendary RAMbow (no schematics or picture exist the original board).<br>



## Bill of materials
| Qt. |    Description     |             Designator          |    Mouser Part     |             Note              |
|:---:|--------------------|---------------------------------|--------------------|-------------------------------|
|10   |Cap. 220 nF 50V     |C1-C9,C18                        |C430C224Z5U5TA      |                               |
|1    |Cap. 10uF 50V       |C17                              |MAL213831109E3      |                               |
|5    |Cap. 47nF 50V       |C12-C16                          |C410C473Z5U5TA      |                               |
|2    |Cap. 10nF 50V       |C10,C11                          |C410C103Z5U5TA      |                               |
|1    |Bead Ferrite        |FB1                              |2743002112          |                               |
|2    |Rnet 9x1kΩ 10 pin   |RN1,RN2                          |4610X-101-102LF     |                               |
|1    |Rnet 9x4.7kΩ 10 pin |RN3                              |4610X-AP1-472LF     |                               |
|10   |R 39Ω               |R2-R11                           |CFR-25JB-52-39R     |                               |
|3    |R 470Ω              |R12-R14                          |CFR-25JB-52-470R    |                               |
|1    |R 100Ω              |R1                               |CFR-25JR-52-100R    |                               |
|3    |R 47Ω               |R15-R17                          |CFR-25JB-52-47R     |                               |
|2    |2 pin header        |JP1,JP2                          |67996-102HLF        |                               |
|2    |2 pin jumper shunt  |JP1,JP2                          |SNT-100-BL-T        |                               |
|1    |025X025 REC 2X30P   |J1                               |5-102766-4          |                               |
|9    |18P DIP SKT         |E16-E24                          |1-2199298-5         |                               |
|1    |40P DIP SKT         |E26                              |1-2199299-5         |                               |
|1    |20P DIP SKT         |E28                              |1-2199298-6         |                               |
|1    |40P IDC CONN M      |J2                               |3-1761605-3         |                               |
|1    |40P DIP IDC SKT     |J2                               |CWR-130-40-0000     |                               |
|1    |40P IDC CONN F      |J2                               |D89140-0101HK       |                               |
|1    |40P IDC Flat cable  |J2                               |                    | you can use an old IDE cable  |
|1    |GAL 16V8            |E28                              |ATF16V8CZ-15PU      | need programmer like TL866    |
|2    |74LS04              |E1,E7                            |SN74LS04N           |                               |
|3    |74LS258             |E2,E3,E15                        |SN74LS258BN         |                               |
|2    |74LS393             |E4,E25                           |SN74LS393N          |                               |
|2    |74LS244             |E5,E14                           |SN74LS244N          |                               |
|1    |74LS245             |E6                               |SN7LS245N           |                               |
|1    |74LS27              |E8                               |SN74LS27N           |                               |
|1    |74LS280             |E9                               |SN74LS280N          |                               |
|1    |74LS125             |E10                              |SN74LS125AN         |                               |
|1    |74LS00              |E11                              |SN74LS00N           |                               |
|1    |74LS03              |E12                              |SN74LS03N           |                               |
|1    |74LS74              |E13                              |SN74LS74AN          |                               |
|1    |74LS373             |E27                              |SN74LS373N          |                               |
|9    |1Mbit DRAM 41024    |E16-E24                          |HM511000AP-8        | from ebay or [utsource](https://www.utsource.net)|

<br>

## Jumper set-up
Only a jumper need to setup, JP2 is closed when RAMbow is installed on rev A or open in rev B.<br>
JP1 is always closed.

## Building notes
As you can see from the picture the IDC cable of the J2 connector that is used to relocate the CPU requires a bit of attention in construction<br><br>
![alt text](https://github.com/na103/rambow/blob/main/img/board.jpg "rambow installed")<br>
the length of the cable must be 85mm and you must separate the individual wires with a cutter to make the cable more flexible.<br>
the operation requires a little attention to avoid cutting the copper insulation.<br>
even closing the socket with pressure requires a fair amount of force, help yourself with some tool<br>

![alt text](https://github.com/na103/rambow/blob/main/img/cpu_idc_skt_1.jpg "CPU Socket relocator")
<br>

## Compatibility and issues

I have successfully tested RAMbow on rev. A and rev. B. with the following operating systems:<br>
MSDOS 3.10<br>
MSDOS 2.10<br>
CP/M-86/80 2.10<br>
CP/M-86/80 2.0<br>
I have not encountered any kind of problem, both rev A and rev B have 896Kb of memory available.<br>
After building RAMbow you can test it with the diagnostic software for memory expansion rev B that you can find [here](https://github.com/na103/rainbow100-memory/tree/main/software)<br><br>
![alt text](https://github.com/na103/rambow/blob/main/img/test_revB.jpg "Memory Test rev B")
![alt text](https://github.com/na103/rambow/blob/main/img/test_revA.jpg "Memory Test rev A")

## Thanks
Thankyou to all the people who have helped with this project.<br>
Bigfix for sharing the DEC schematics of the 8087 adapter.<br>
N. Brown and Alitel for actively participating with their ideas in the [VCFED forum thread.](https://forum.vcfed.org/index.php?threads/rainbow-100a-memory-beyond-256k.1247302/)<br>
Claudio Parmigiani for the valuable advice<br>

If you found this my work useful, please consider buying me a cup of coffee if you want:<br>
<a href='https://ko-fi.com/na103' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://storage.ko-fi.com/cdn/cup-border.png' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

# License

This work is licensed under a Creative Commons Attribution 4.0 International License. See [https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/).
