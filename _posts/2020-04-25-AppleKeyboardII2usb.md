---
layout: post
title: "Using an old ADB Apple Keyboard II on USB computers"
categories:
  - Old Computer
tags:
  - keyboard
  - adb
  - usb
  - teensy
  - upcycle
---

## The keyboard and the goal :keyboard:
The keyboard is an ADB *Apple Keyboard II*, with the french layout. 
This keyboard was laying around, not used anymore (old world Mac), but sill in good shape.

The goal is to use it on any everyday modern computer.
It's an upcycling challenge!

## Binaries and installation
To build an ADB <-> USB converter, the following items are needed :
- Teensy 2.0 (or whatever board with Atmega 32U4)
- Mini-din 4 female connector
- 1-10 kOhms pull-up resistor

The female ADB connector is soldered to the microcontroller with respect to 
the following pin out.The pull-up resistor is soldered between the DATA and the 
VCC pins.

```
ADB female socket from the front :

  ,--_--.		                   ATmega 32U4 Pin
 / o4 3o \      1: DATA         PD0, D3 (arduino micro clone)
| o2   1o |     2: Power SW 	PD1
 -  ===  -      3: VCC
  `-___-'       4: GND
```

The firmware program to decode the key sended by the keyboard is built with 
[`tmk_keyboard`](https://github.com/tmk/tmk_keyboard) software and need 
to be upload with Teensy Loader.

[adb_usb_rev1_akIIfr_2.hex](assets/2020-04-25-bin/adb_usb_rev1_akIIfr_2.hex)

Since the keyboard has a French Mac Layout, some adjustments have been made to 
the Windows input method. Find below the installer. After a restart the input 
method is accessible through the `meta` + `space` keys.

[AppleKeyboardII_Layout.zip](assets/2020-04-25-bin/AppleKeyboardII_Layout.zip)

And voilà, you can type with your old keyboard!

## Bonus

ADB is also compatible with the mouse. So the old 1 button apple mouse works also.


## Final thoughts

This post was typed with the AKII. It was very comfortable and easy to write.

Some features need new habits. For example arrows are placed in a strange way, 
because of the small form factor of the keyboard. But since the keyboard has a 
keypad it's possible to use the arrow with the `shift` modifier.
 The `first`, `end`, `page up` and `page down` are also accessible
 that way. And finally, on Macintosh the `alt gr` key does not exist but 
 `alt` + `crtl` does the same.

The only missing feature is the `suppr` key :'( and I note that I use it quite 
a lot.


## Compilation and tools used

Here are the instructions to install the tools and build the binary on Windows.

### AVR Toolchain

To compile the software the `AVR Toolchain` from Atmel is needed, now 
distributed by Microchip, 
[AVR and Arm Toolchains](https://www.microchip.com/mplab/avr-support/avr-and-arm-toolchains-c-compilers).
 The tool chain is installed to the directory `avr_toolchain`.

The directory `avr_toolchain\bin` must be registered in the `PATH` variable, in 
the environment variables from Windows.

### Installation and compilation of `tmk_keyboard`

Clone the repo  with `git clone` :
```
git clone https://github.com/tmk/tmk_keyboard
```
Update the submodule with :
```
git submodule update --init
```

For ADB go to `tmk_keyboard/converter/adb_usb/` and run the following commands :
```
make -f Makefile.rev1 KEYMAP=akIIfr
```

The KEYMAP is downloadable here 
[unimap_akIIfr.c](assets/2020-04-25-bin/unimap_akIIfr.c).
 Only one key has been changed, the key `PEQL` to `SLSH`, in order to have for 
 the `=` of the keypad the same key next to right shift.
 
The hex file is then upload to the Teensy with the Teensy loader.

### Mac Keymap

The Mac keymap for french layout is a bit specific. 
The [Microsoft Keyboard Layout Editor](https://www.microsoft.com/en-us/download/details.aspx?id=22339)
 is used to create this specific keymap.

To install the sofwtare, the .NET framework 2.0 is required. The automatic downloader
 doesn't work. Here is the [link](https://www.microsoft.com/en-us/download/details.aspx?id=6523)
 to find it on Microsoft website.