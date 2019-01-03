# Marlin 3D Printer Firmware

This version is modified to work with the my specific ANet A8 which has a bltouch sensor mounted on it. 

[BLTouch Sensor on AliExpress](https://www.aliexpress.com/item/Hot-Auto-Leveling-Sensor-3D-Touch-for-3D-Printer-Improve-Printing-Precision-Auto-Bed-Leveling-Touch/32785161882.html?spm=2114.search0104.3.8.67f23d88iyfQoy&ws_ab_test=searchweb0_0,searchweb201602_5_10065_10130_10068_10890_10547_319_10546_317_10548_10545_10696_453_10084_454_10083_10618_10307_537_536_10059_10884_10887_100031_321_322_10103,searchweb201603_52,ppcSwitch_0&algo_expid=c7c4adf5-aece-49ea-8433-66bf31560e1c-1&algo_pvid=c7c4adf5-aece-49ea-8433-66bf31560e1c)

[Mount I used](https://www.thingiverse.com/thing:1846913)

## Setup Instructions

Physical Install

1. Mount and wire as per mount design and wiring diagram.

Firmware Upgrade

The code in this repo has already had these steps applied, but steps 9/10 you will have to do again.

	1. Download the Marlin firmware from marlinfw.org. 1.1.9 is production ready.
	2. Copy the A8 Config over from the config examples folder.
	3. http://github.com/Skynet3D/anet-board and download the board files into the arduino libraries. (Documents/Arduino/libraries )
	4. Open up the Arduino IDE
	5. Go into Arduino IDE and pick a8 board ( NOT optiboot ).
	6. Open the marlin.ino in the marlin firmware folder.
	7. Navigate to Configuration.h.
	8. Find //#define BLTOUCH, uncomment, below it add#define SERVO0_PIN 27
	9. Find "x_probe"
	10. Following the diagram, measure the offsets and put them in as provided. For X/Y I used a piece of paper and marked out the points. For Z I used credit cards as shims.
	11. Uncomment Z_SAFE_HOMING to enable.
	12. Z_MIN_PROBE_ENDSTOP_INVERTING from true to false
	13. #define AUTO_BED_LEVEL_BILINEAR
	14. Upload firmware!
	15. Open up the serial terminal in Arduino. ( Baud should be 115200 )
	16. Run G-Code 502 then 500 to reset defaults in EEPROM.
        17. Run bed leveling from printer GUI.

## Marlin 1.1

Marlin 1.1 represents an evolutionary leap over Marlin 1.0.2. It is the result of over two years of effort by several volunteers around the world who have paid meticulous and sometimes obsessive attention to every detail. For this release we focused on code quality, performance, stability, and overall user experience. Several new features have also been added, many of which require no extra hardware.

For complete Marlin documentation click over to the [Marlin Homepage <marlinfw.org>](http://marlinfw.org/), where you will find in-depth articles, how-to videos, and tutorials on every aspect of Marlin, as the site develops. For release notes, see the [Releases](https://github.com/MarlinFirmware/Marlin/releases) page.

The 1.1.x branch is home to all tagged releases of Marlin 1.1 (final version 1.1.9 – August 2018).

This branch will receive no further updates. All future development —including all bug fixes— will take place in the [`bugfix-2.0.x`](https://github.com/MarlinFirmware/Marlin/tree/bugfix-2.0.x) branch, which will also serve as the root for all future Marlin development. Be sure to test [`bugfix-2.0.x`](https://github.com/MarlinFirmware/Marlin/tree/bugfix-2.0.x) before reporting any bugs you find in 1.1.9.

Marlin 1.1.9 is the final release of the 8-bit flat version of Marlin Firmware. A monumental amount of talent and effort has gone into its production, and thanks are due to many people around the world. Throughout Marlin 1.1 development we worked closely with the community, contributors, vendors, host developers, library developers, etc. to improve the quality, configurability, and compatibility of Marlin Firmware, all while continuing to support a wide variety of Arduino-based boards.

## Marlin 1.0.x

Previous releases of Marlin include [1.0.2-2](https://github.com/MarlinFirmware/Marlin/tree/1.0.2-2) (December 2016) and [1.0.1](https://github.com/MarlinFirmware/Marlin/tree/1.0.1) (December 2014). Any version of Marlin prior to 1.0.1 (when we started tagging versions) can be collectively referred to as Marlin 1.0.0.

## Contributing to Marlin

Click on the [Issue Queue](https://github.com/MarlinFirmware/Marlin/issues) and [Pull Requests](https://github.com/MarlinFirmware/Marlin/pulls) links above at any time to see what we're currently working on.

To submit patches and new features for Marlin 1.1 check out the [bugfix-1.1.x](https://github.com/MarlinFirmware/Marlin/tree/bugfix-1.1.x) branch, add your commits, and submit a Pull Request back to the `bugfix-1.1.x` branch. Periodically that branch will form the basis for the next minor release.

Note that our "bugfix" branch will always contain the latest patches to the current release version. These patches may not be widely tested. As always, when using "nightly" builds of Marlin, proceed with full caution.

## Current Status: In Development

Marlin development has reached an important milestone with its first stable release in over 2 years. During this period we focused on cleaning up the code and making it more modern, consistent, readable, and sensible.

## Future Development

Marlin 1.1 is the last "flat" version of Marlin!

Arduino IDE now has support for folder hierarchies, so Marlin 1.2 will have a [hierarchical file structure](https://github.com/MarlinFirmware/Marlin/tree/breakup-marlin-idea). Marlin's newly reorganized code will be easier to work with and form a stronger starting-point as we get into [32-bit CPU support](https://github.com/MarlinFirmware/Marlin/tree/32-Bit-RCBugFix-new) and the Hardware Access Layer (HAL).

[![Coverity Scan Build Status](https://scan.coverity.com/projects/2224/badge.svg)](https://scan.coverity.com/projects/2224)
[![Travis Build Status](https://travis-ci.org/MarlinFirmware/Marlin.svg)](https://travis-ci.org/MarlinFirmware/Marlin)

## Marlin Resources

- [Marlin Home Page](http://marlinfw.org/) - The Marlin Documentation Project. Join us!
- [RepRap.org Wiki Page](http://reprap.org/wiki/Marlin) - An overview of Marlin and its role in RepRap.
- [Marlin Firmware Forum](http://forums.reprap.org/list.php?415) - Find help with configuration, get up and running.
- [@MarlinFirmware](https://twitter.com/MarlinFirmware) on Twitter - Follow for news, release alerts, and tips & tricks. (Maintained by [@thinkyhead](https://github.com/thinkyhead).)

## Credits

The current Marlin dev team consists of:
 - Roxanne Neufeld [[@Roxy-3D](https://github.com/Roxy-3D)]
 - Scott Lahteine [[@thinkyhead](https://github.com/thinkyhead)]
 - Bob Kuhn [[@Bob-the-Kuhn](https://github.com/Bob-the-Kuhn)]

Notable contributors include:
 - Alberto Cotronei [[@MagoKimbra](https://github.com/MagoKimbra)]
 - Andreas Hardtung [[@AnHardt](https://github.com/AnHardt)]
 - Bernhard Kubicek [[@bkubicek](https://github.com/bkubicek)]
 - Bob Cousins [[@bobc](https://github.com/bobc)]
 - Chris Palmer [[@nophead](https://github.com/nophead)]
 - David Braam [[@daid](https://github.com/daid)]
 - Edward Patel [[@epatel](https://github.com/epatel)]
 - Erik van der Zalm [[@ErikZalm](https://github.com/ErikZalm)]
 - Ernesto Martinez [[@emartinez167](https://github.com/emartinez167)]
 - F. Malpartida [[@fmalpartida](https://github.com/fmalpartida)]
 - Jochen Groppe [[@CONSULitAS](https://github.com/CONSULitAS)]
 - João Brazio [[@jbrazio](https://github.com/jbrazio)]
 - Kai [[@Kaibob2](https://github.com/Kaibob2)]
 - Luc Van Daele[[@LVD-AC](https://github.com/LVD-AC)]
 - Nico Tonnhofer [[@Wurstnase](https://github.com/Wurstnase)]
 - Petr Zahradnik [[@clexpert](https://github.com/clexpert)]
 - Thomas Moore [[@tcm0116](https://github.com/tcm0116)]
 - [[@alexxy](https://github.com/alexxy)]
 - [[@android444](https://github.com/android444)]
 - [[@benlye](https://github.com/benlye)]
 - [[@bgort](https://github.com/bgort)]
 - [[@ejtagle](https://github.com/ejtagle)]
 - [[@Grogyan](https://github.com/Grogyan)]
 - [[@marcio-ao](https://github.com/marcio-ao)]
 - [[@maverikou](https://github.com/maverikou)]
 - [[@oysteinkrog](https://github.com/oysteinkrog)]
 - [[@p3p](https://github.com/p3p)]
 - [[@paclema](https://github.com/paclema)]
 - [[@paulusjacobus](https://github.com/paulusjacobus)]
 - [[@psavva](https://github.com/psavva)]
 - [[@Tannoo](https://github.com/Tannoo)]
 - [[@teemuatlut](https://github.com/teemuatlut)]
 - ...and many others

## License

Marlin is published under the [GPL license](https://github.com/COPYING.md) because we believe in open development. The GPL comes with both rights and obligations. Whether you use Marlin firmware as the driver for your open or closed-source product, you must keep Marlin open, and you must provide your compatible Marlin source code to end users upon request. The most straightforward way to comply with the Marlin license is to make a fork of Marlin on Github, perform your modifications, and direct users to your modified fork.

While we can't prevent the use of this code in products (3D printers, CNC, etc.) that are closed source or crippled by a patent, we would prefer that you choose another firmware or, better yet, make your own.

[![Flattr this git repo](http://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=ErikZalm&url=https://github.com/MarlinFirmware/Marlin&title=Marlin&language=&tags=github&category=software)
