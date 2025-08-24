# Genesis / Mega Drive Advanced UV Cart - UNDER CONSTRUCTION

# Order at your own risk. These are technically untested.

This is a Sega Genesis/Mega Drive cartridge circuit board design that uses the older UV EPROMs, 27C322 or 27C160. This is the updated version of my existing carts, ported from Eagle to KiCad with some minor changes, but fully open source. With this board, unlike the flash version, you need to program the EPROM before soldering to the board. This cartridge is made entirely from **off the shelf components.** No donors are required.

<img width="2364" height="1308" alt="image" src="https://github.com/user-attachments/assets/c07589b4-09a4-4488-b5af-e02cd7d18901" />

This cartridge covers over 95% of the entire Genesis library. You can backup games up to 4 MB in size, with up to 32 KB RAM. It can also handle any ROM hack that falls into these limits, including the ever popular <a href="https://info.sonicretro.org/Sonic_3_Complete">Sonic 3 Complete</a>. Check out the <a href="https://github.com/MouseBiteLabs/Genesis-Cartridges/wiki/Game-Compatibility">Game Compatibility</a> page in the wiki for more info.

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

**I sell this blank circuit board on Etsy, so you don't have to buy a bunch of multiples if you don't want to.** (Click the banner!) [Not yet live]

<a href="https://mousebitelabs.etsy.com"><img src="https://github-production-user-asset-6210df.s3.amazonaws.com/97127539/239718536-5c9aefe3-0628-4434-b8d8-55ff80ac3bbc.png" alt="PCB from Etsy" /></a> 

You can use the zipped folder at any board fabricator you like. You may also buy the board from PCBWay using this link (disclosure: I receive 10% of the sale value to go towards future PCB orders of my own):

<a href="https://www.pcbway.com/project/shareproject/Genesis_Mega_Drive_Advanced_UV_EPROM_Cartridge_2a6a0bd7.html"><img src="https://www.pcbway.com/project/img/images/frompcbway-1220.png" alt="PCB from PCBWay" /></a>

<a href="https://oshpark.com/shared_projects/QJOp6D4P">This board can also be ordered from OSH Park,</a> but you should sand down the edges of the cartridge to chamfer them yourself before inserting them in a console.

<img width="1024" height="512" alt="image" src="https://github.com/user-attachments/assets/2300fe96-6ca6-4500-a0a3-ee543712809f" />

<a href="https://www.retrorgb.com/determining-the-build-quality-of-a-game-cartridge.html">(Image taken from RetroRGB)</a>

## Required Equipment

- You will need basic tools and supplies, like a soldering iron, solder, and flux.
- You need a way to program the ROM chip(s). There are two ways I have programmed them in the past:
  - Using the <a href="https://xgecu.myshopify.com/products/xgecu-new-t48-tl866-3gprogrammer-v12-01-support-28000-ics-for-spi-nor-nand-flash-emmc-bga153-162-169-100-221-tsop-sop-plcc">T48 programmer</a> with my <a href="https://github.com/MouseBiteLabs/27C322-TL866-Adapter">27C322 to TL866 Programming Adatper</a> board. The programming adapter is compatible with the T48, and it allows you to program the 42-pin EPROMs (27C160 and 27C322) with the 40-pin T48 programmer.
  OR
  - Using the <a href="https://www.mcumall.com/store/index.php?route=product/product&path=66&product_id=85">GQ4x4 programmer</a> with the ZIF adapter board that comes with it.

## How to Program

<a href="https://github.com/MouseBiteLabs/Genesis-Cartridges/wiki/Programming-UV-EPROMs">Please check out the wiki pages on how to prepare the ROM and program the cartridge.</a>

## Board Configurations

You *may not* need every single part on this board to make a game. The game you want to make is mainly dependent on the ROM size and the RAM size (if any). Depending on your needs, you only need to solder on certain components, which you can find below in the BOM section.

- **Every board needs Group A components.** You can make games that have no RAM and are up to 4 MB large with this configuration.
- If you need RAM space, **add Group C components.** This will add 32 KB of RAM space.
- If your game is larger than 2 MB and uses any amount of SRAM, **add Group D components.**

<a href="https://github.com/MouseBiteLabs/Genesis-Cartridges/wiki/Advanced-UV">Check out the wiki for visual examples.</a>

### Picking an EPROM, and ROM Size Selection Pads

If your game is only 2 MB large or less, you can use a 27C160. If your game is larger than 2 MB (but 4 MB or less), then you need to use a 27C322. These parts are only available second-hand on places like AliExpress or eBay.

The setting you need to choose for these jumpers is pretty self-explanatory - **keep in mind, this is the size of the ROM file, *not* the amount of ROM space you have available on the board.** If you have a 27C322, for example, but your ROM file is only 2 MB, you need to configure the board to the "less than or equal to 2 MB" setting. Also, these pads are only required to be configured if your board uses any amount of SRAM - ROM-only boards do not utilize this setting (but it won't hurt to solder the proper selection anyway).

<img width="662" height="208" alt="image" src="https://github.com/user-attachments/assets/b38e82c8-db2b-493b-87aa-caf3b5e54963" />

### Bypass Solder Jumper

If your game does not use SRAM, you will not need U4 but you need to bridge the solder jumper instead.

<img width="490" height="233" alt="image" src="https://github.com/user-attachments/assets/ead27a8a-c3d1-449b-9f26-211f9e14660b" />

## Estimating Battery Life

Measure the voltage across R1 using a multimeter in DC mV mode, touching the probes to either the leads on R1 or the pads on the back of the board for R1. You should read something around 1 mV or less. If you are severely higher than 1 mV, like in the 10's of mV, then you have a problem on your board.

Once you have a suitable voltage, find the milliamp-hour rating of your selected battery (preferrably from a datasheet). For example, a Renata CR2032 battery is rated for 225 mAh.

Now to estimate battery life, take the voltage measurement in mV and the battery rating in mAh, and plug it into this equation: 

Time (years) = Resistance of R1 (ohms) * Battery capacity (mAh) / Voltage (mV) / 8760

The factor of 8760 is for converting years to hours (24 hours in a day, 365 days in a year). The resistance of R1 is 1000 ohms. So for an example, if you measured 1 mV on R1 and are using a Renata CR2032, you would get 1000 * 225 / 1 / 8760 = **25.7 years.**

## Bill of Materials (BOM)

The component groups required for the build you want to make are detailed above.

### Mouser Shopping Cart

The following cart has *the maximum amount* of parts you would potentially need on a single board, plus a few extras of the passive components due to price breaks. You can remove the chips you don't need from the shopping cart before ordering, according to the component group assignments below.

[mouser cart]

The parts in this cart are for the through-hole versions of the parts, but there are pads if you want to use surface mount instead for the resistors, capacitors, diodes, and transistor.

### Group A - 2 MB ROM, No RAM

| Reference | Value/Part Number | Package       | Description                     | Source                      |
| --------- | ----------------- | ------------- | ------------------------------- | --------------------------- |
| C1        | 0.1uF             | 2.5mm spacing | Capacitor (MLCC)                | https://mou.sr/3JoDO29      |
| CC        | 22uF              | 5mm x 5mm     | Aluminum Electrolytic Capacitor | https://mou.sr/4moiXKK      |
| U1        | 27C160 / 27C322   | DIP-42        | UV EPROM                        | Search on Aliexpress, eBay  |

### Group C - Adds 32 KB of RAM for games with 2 MB of ROM or less in size

| Reference | Value/Part Number | Package  | Description                     | Source                  |
| --------- | ----------------- | -------- | ------------------------------- | ----------------------- |
| B1        | CR2032       | CR2032        | Coin Cell Battery               | https://mou.sr/3QhcXXc  |
| C2        | 0.1uF        | 2.5mm spacing | Capacitor (MLCC)                | https://mou.sr/3JoDO29  | 
| C4        | 0.1uF        | 2.5mm spacing | Capacitor (MLCC)                | https://mou.sr/3JoDO29  |
| CB        | 22uF         | 5mm x 5mm     | Aluminum Electrolytic Capacitor | https://mou.sr/4moiXKK  |
| D1        | BAT85        | DO-35-2       | Diode                           | https://mou.sr/49GVT4m  |
| D2        | BAT85        | DO-35-2       | Diode                           | https://mou.sr/49GVT4m  |
| D3        | BAT85        | DO-35-2       | Diode                           | https://mou.sr/49GVT4m  |
| Q1        | 2N3904       |               | Transistor (NPN)                |                                                  |
| R1        | 1k           |               | Resistor                        |                                                  |
| R2        | 100k         |               | Resistor                        |                                                  |
| R3        | 10k          |               | Resistor                        |                                                  |
| R4        | 1k           |               | Resistor                        |                                                  |
| R5        | 10k          |               | Resistor                        |                                                  |
| U2        | AS6C62256    | DIP-28        | SRAM                            | https://mou.sr/3HlZ0mh                           |
| U4        | 74HCT139     | DIP-16        | Decoder                         |                                                  |

### Group D - Adds capability for larger games to utilize RAM

| Reference | Value/Part Number | Package   | Description      | Source                                           |
| --------- | ----------------- | --------- | ---------------- | ------------------------------------------------ |
| C3        | 0.1uF             | 2.5mm spacing | Capacitor (MLCC) | https://mou.sr/3JoDO29                       |
| U3        | 74HCT74           | DIP-14        | Flip-Flop        |                                              |

## Adding LEDs

There are 10 spots around the border of the board on the front and back for LEDs. This includes pads for an 0603 size resistor and 0603 size LED, powered by the 5V rail. Resistor and LED selection will vary based on your own preferences, so you will have to experiment with values yourself.

## Revision History

### v1.1 - Release

- Fixed /WR hole location to not overlap silkscreen

### v1.0 - Alpha

- Prototype version

## Acknowledgements

- Continual thanks to all in the nesdev community for their resources, design tips, and support throughout the past half-decade.

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you **must** give appropriate credit, provide a link to the license, and indicate if any changes were made.

©MouseBiteLabs 2025

