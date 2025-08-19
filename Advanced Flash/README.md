# Genesis / Mega Drive Advanced Flash Cart

This is a Sega Genesis/Mega Drive cartridge circuit board design that is capable of being flashed via the <a href="https://github.com/sanni/cartreader">Open Source Cart Reader (OSCR) by sanni</a>. Alternatively, you can also flash the ROM chips before soldering them to the board through the use of a programmer like the <a href="https://xgecu.myshopify.com/products/xgecu-new-t48-tl866-3gprogrammer-v12-01-support-28000-ics-for-spi-nor-nand-flash-emmc-bga153-162-169-100-221-tsop-sop-plcc">T48 programmer</a> with the <a href="https://xgecu.myshopify.com/products/100-original-xgecu-adp_f48_ex-1-tsop48-special-adapter-for-nor-flash-only-use-on-t48-tl866-3g-programmer">TSOP48 adapter</a>. This cartridge is made entirely from **brand new off the shelf components.** No donors are required, and you don't need to rely on AliExpress or eBay for parts!

<img width="1281" height="934" alt="image" src="https://github.com/user-attachments/assets/154fa493-7542-434d-af7e-0724f76a0b3e" />

This cartridge covers over 95% of the entire Genesis library. You can backup games up to 4 MB in size, with up to 32 KB RAM. It can also handle any ROM hack that falls into these limits, including the ever popular <a href="https://info.sonicretro.org/Sonic_3_Complete">Sonic 3 Complete</a>.

All gerbers and source files can be found in this repo, as this project is fully open source. Please read all instructions before attempting the project.

## Important Things Before You Start

1) <a href="https://github.com/MouseBiteLabs/Genesis-Cartridges/wiki">Please review the wiki for more information about using the circuit boards, instructions for how to program them, and example builds.</a>
2) When soldering parts on, it's a good idea to put kapton tape or otherwise cover the bottom cartridge edge. You do not want to get solder on the cartridge contacts.
3) I am not responsible for any damage you do to your self or your property. Attempt this project at your own risk.
4) I do not guarantee design compatibility. You may encounter issues with certain games. There is also a chance I have made an error in the design or the BOM - if this is the case, I will do everything I can to address the problem as quickly as possible.
5) If you are using this board to make games other than for personal use, you must have permission from the originator to use and distribute any ROM images or other related material. You are responsible for making sure you adhere to any license requirements.

DO NOT use my circuit boards for profiting from stolen work - this especially includes homebrew content, ROM hacks, and using fan-made labels without permission from the originator. **Support ALL original creators!**

## Board Characteristics and Order Information

The zipped folder contains all the gerber files for this board. The following options **must** be chosen when ordering boards for yourself.

- Thickness: 1.6mm
- Surface Finish: ENIG
- Gold Fingers: Yes, 30° chamfer

**I sell this blank circuit board on Etsy, so you don't have to buy a bunch of multiples if you don't want to.** (Click the banner!)

**[Not yet live, these are placeholders]**

<a href="https://mousebitelabs.etsy.com"><img src="https://github-production-user-asset-6210df.s3.amazonaws.com/97127539/239718536-5c9aefe3-0628-4434-b8d8-55ff80ac3bbc.png" alt="PCB from Etsy" /></a> 

You can use the zipped folder at any board fabricator you like. You may also buy the board from PCBWay using this link (disclosure: I receive 10% of the sale value to go towards future PCB orders of my own):

<a href="https://www.pcbway.com/"><img src="https://www.pcbway.com/project/img/images/frompcbway-1220.png" alt="PCB from PCBWay" /></a>

## Required Equipment

- You will need basic tools, like a soldering iron, hot plate, and/or hot air rework station.
- You need a way to program the ROM chip(s).
  - This can be done with the <a href="https://github.com/sanni/cartreader">OSCR</a> to load the game and save data onto the catridge, after the cartridge is assembled.
  - Alternatively, the <a href="https://xgecu.myshopify.com/products/xgecu-new-t48-tl866-3gprogrammer-v12-01-support-28000-ics-for-spi-nor-nand-flash-emmc-bga153-162-169-100-221-tsop-sop-plcc">T48 programmer</a> with the <a href="https://xgecu.myshopify.com/products/100-original-xgecu-adp_f48_ex-1-tsop48-special-adapter-for-nor-flash-only-use-on-t48-tl866-3g-programmer">TSOP48 adapter</a> can program the ROM chip(s). The downside to this is that if you screw up the programming, you'll have to desolder the chips and program them again.

## How to Program

<a href="https://github.com/MouseBiteLabs/Genesis-Cartridges/wiki/Preparing-the-ROM">Please check out the wiki pages on how to prepare the ROM and program the cartridge.</a>

## Board Configurations

You *do not* need every single part on this board to make a game. The game you want to make is mainly dependent on the ROM size and the RAM size (if any). Depending on your needs, you only need to solder on certain components, which you can find below in the BOM section.

- **Every board needs Group A components.** You can make games that have no RAM and are up to 2 MB large with this configuration.
- If you want to expand the ROM space to a full 4 MB, **add Group B components**.
- If you need RAM space, **add Group C components.** This will add 32 KB of RAM space.
- If your game is larger than 2 MB and uses any amount of SRAM, **add Group D components.**

### Bypass Solder Jumpers

If your game is only 2 MB large, you will not need U3. There is a solder jumper inside the U3 footprint that needs to be bridged if this is the case.

<img width="235" height="228" alt="image" src="https://github.com/user-attachments/assets/aa87a7dd-83f4-456b-b738-3f10394fd005" />

Similarly, if your game does not use SRAM, you will not need U7 but you need to bridge the solder jumper instead.

<img width="256" height="227" alt="image" src="https://github.com/user-attachments/assets/a0a02e0b-db57-4fa9-b0d8-2e91309fb8f2" />

### ROM Size Selection (SW1)

There is only one switch on this board for configuration purposes, and the setting you need to choose is pretty self-explanatory. You can either use an SPDT switch (part number shown in BOM below), or if you do not plan to reflash the board with a differently sized game in the future, you can hard-wire the selection. **This switch is only required to be configured if your board uses any amount of SRAM - ROM-only boards do not utilize this setting.**

In the image below, the "less than or equal to 2MB" option is selected in both cases. The resistor on the right is a zero-ohm jumper (or you can use a solder blob).

<img width="1597" height="632" alt="image" src="https://github.com/user-attachments/assets/1ca78731-4d9a-4134-a979-2c00d1608bc3" />

## Estimating Battery Life

To accurately estimate the battery life, you must first solder the battery in, and then either program your game in the OSCR or power it on in a console.

After that, measure the voltage across R1 (either on the part itself or on the + and - pads on the back of the board) using a multimeter in DC mV mode, touching the probes to the two test point pads on either side of R1. You should read something around 1 mV or less. If you are severely higher than 1 mV, like in the 10's of mV, then you have a problem on your board.

Once you have a suitable voltage, find the milliamp-hour rating of your selected battery (preferrably from a datasheet). For example, a Renata CR2032 battery is rated for 225 mAh.

Now to estimate battery life, take the voltage measurement in mV and the battery rating in mAh, and plug it into this equation: 

Time (years) = Resistance of R1 (ohms) * Battery capacity (mAh) / Voltage (mV) / 8760

The factor of 8760 is for converting years to hours (24 hours in a day, 365 days in a year). The resistance of R1 is 1000 ohms. So for an example, if you measured 1 mV on R1 and are using a Renata CR2032, you would get 1000 * 225 / 1 / 8760 = **25.7 years.**

## Bill of Materials (BOM)

The component groups required for the build you want to make are detailed above.

### Mouser Shopping Cart

The following cart has *the maximum amount* of parts you would potentially need on a single board, plus a few extras of the passive components due to price breaks. You can remove the chips you don't need from the shopping cart before ordering, according to the component group assignments below.

https://www.mouser.com/ProjectManager/ProjectDetail.aspx?AccessID=ea748d2d57

### Group A - 2 MB ROM, No RAM

| Reference | Value/Part Number | Package | Description      | Source                                           |
| --------- | ----------------- | ------- | ---------------- | ------------------------------------------------ |
| C1        | 0.1uF             | 0603    | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| CC        | 22uF              | 1206    | Capacitor (MLCC) | [https://mou.sr/4e4zShm](https://mou.sr/4e4zShm) |
| U1        | M29F160           | TSOP-48 | Flash EEPROM     | [https://mou.sr/3HIjb09](https://mou.sr/3HIjb09) |

### Group B - Adds 2 MB of ROM

| Reference | Value/Part Number | Package  | Description      | Source                                           |
| --------- | ----------------- | -------- | ---------------- | ------------------------------------------------ |
| C2        | 0.1uF             | 0603     | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C3        | 0.1uF             | 0603     | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| U2        | M29F160           | TSOP-48  | Flash EEPROM     | [https://mou.sr/3HIjb09](https://mou.sr/3HIjb09) |
| U3        | 74HCT139          | TSSOP-16 | Decoder          | [https://mou.sr/4eqzppn](https://mou.sr/4eqzppn) |

### Group C - Adds 32 KB of RAM for games with 2 MB of ROM or less in size

| Reference | Value/Part Number | Package  | Description        | Source                                           |
| --------- | ----------------- | -------- | ------------------ | ------------------------------------------------ |
| B1        | CR2032            | CR2032   | Coin Cell Battery  | [https://mou.sr/3QhcXXc](https://mou.sr/3QhcXXc) |
| C4        | 0.1uF             | 0603     | Capacitor (MLCC)   | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C5        | 0.1uF             | 0603     | Capacitor (MLCC)   | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C7        | 0.1uF             | 0603     | Capacitor (MLCC)   | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| CB        | 22uF              | 1206     | Capacitor (MLCC)   | [https://mou.sr/4e4zShm](https://mou.sr/4e4zShm) |
| R1        | 1k                | 0603     | Resistor           | [https://mou.sr/3U0EvS4](https://mou.sr/3U0EvS4) |
| R2        | 130k              | 0603     | Resistor           | [https://mou.sr/3MjXliy](https://mou.sr/3MjXliy) |
| R3        | 49.9k             | 0603     | Resistor           | [https://mou.sr/3BBcDgp](https://mou.sr/3BBcDgp) |
| U4        | AS6C62256         | SOP-28   | SRAM               | [https://mou.sr/4oDz7Bu](https://mou.sr/4oDz7Bu) |
| U5        | TPS3613           | MSOP-10  | Battery Management | [https://mou.sr/45Ir2kh](https://mou.sr/45Ir2kh) |
| U7        | 74HCT139          | TSSOP-16 | Decoder            | [https://mou.sr/4eqzppn](https://mou.sr/4eqzppn) |

### Group D - Adds capability for larger games to utilize RAM

| Reference | Value/Part Number | Package   | Description      | Source                                           |
| --------- | ----------------- | --------- | ---------------- | ------------------------------------------------ |
| C6        | 0.1uF             | 0603      | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| SW1       | CAS-120B          | Gull-wing | SPDT Switch      | [https://mou.sr/4fCZDqy](https://mou.sr/4fCZDqy) |
| U6        | 74HCT74           | TSSOP-14  | Flip Flop        | [https://mou.sr/4mKwqfF](https://mou.sr/4mKwqfF) |

Note: SW1 is optional and can be replaced with solder bridges or zero ohm resistors.

## Adding LEDs

There are 10 spots around the border of the board on the front and back for LEDs. This includes pads for an 0603 size resistor and 0603 size LED, powered by the 5V rail. Resistor and LED selection will vary based on your own preferences, so you will have to experiment with values yourself.

## Revision History

### v1.1 - Release

- Fix LED resistor connections on the back of the board
- Added test points for measuring battery current easier

### v1.0 - Alpha

- Prototype version

## Acknowledgements

- Huge thanks to sanni for firstly creating the OSCR, and secondly for adding programming support for the cartridges.
- Additionally huge thanks to agi from the discord community for his work on adding flash support for these boards to the OSCR! You have made this cartridge so much better through your hard work.
- Continual thanks to all in the nesdev community for their resources, design tips, and support throughout the past half-decade.

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you **must** give appropriate credit, provide a link to the license, and indicate if any changes were made.

©MouseBiteLabs 2025

