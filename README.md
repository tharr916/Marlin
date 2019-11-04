# SKR 1.3 Creality Ender-5 Marlin 2.0.x Firmware

[![Build Status](https://travis-ci.org/tharr916/Marlin.svg?branch=Ender-5-SKR-1.3-TMC2130-Linear-Advance)](https://travis-ci.org/tharr916/Marlin)
![GitHub](https://img.shields.io/github/license/marlinfirmware/marlin.svg)
![GitHub contributors](https://img.shields.io/github/contributors/marlinfirmware/marlin.svg)
![GitHub Release Date](https://img.shields.io/github/release-date/marlinfirmware/marlin.svg)

## Specs

**THIS IS A WIP, BASED ON DOCUMENTATION IN _thisiskeithb's_ 'myskr' REPO**

This firmware is configured for *my* Ender-3 fitted with a BigTreeTech SKR 1.3 and TMC5160s *with* Linear Advance enabled ([demo](https://www.youtube.com/watch?v=o_MTTGHrnHk)) as well as the following mods:

* Hotend
  * [E3D Titan extruder clone](https://wiki.e3d-online.com/Titan_Assembly)
  * [E3D V6 all-metal hotend](https://e3d-online.com/v6-all-metal-hotend) and [plated copper heater block](https://e3d-online.com/v6-plated-copper-heater-block) in direct drive w/ [Petsfang mount](https://www.thingiverse.com/thing:2963434)

  * [Slice Engineering 50w heater cartridge](https://www.sliceengineering.com/shop/50w-heater-cartridge), [450°C/high temperature thermistor](https://www.sliceengineering.com/shop/high-temp-thermistor), and [0.4mm vanadium nozzle](https://www.sliceengineering.com/shop/vanadium-nozzle)
  * [Mechatronics B5015E24B-BSR 24v 5015 fan](https://www.digikey.com/product-detail/en/mechatronics-fan-group/B5015E24B-BSR/1570-1034-ND/5209731) (parts cooling)

* Drivers
  * [Watterott TMC5160s](https://shop.watterott.com/SilentStepStick-TMC5160-Stepper-motor-driver) on X/Y/Z/E
  * [Watterott SilentStepStick Protectors](https://shop.watterott.com/SilentStepStick-Protector-for-Stepper-Motor-Drivers) on X/Y/Z/E

* Steppers/Motors
  * 1/32 microstepping
  * Extruder: [LDO 0.9° pancake motor](https://ldomotors.manufacturer.globalsources.com/si/6008840349362/pdtl/Stepping-motor/1156769667/Nmea17-0.9-degree-hybrid-stepper-motor.htm)
  * X-axis: Creality 42-40/JKong Motor JK42HS40-1004A-02F 1.8° motor (Used as the extruder motor on a stock Ender-3)
  * Y-axis: Anycubic AC-3D651/Busheng 17HD40005-22B, 1.8° motor
  * Z-axis: 2 x Creality 42-34/JKong Motor JK42HS34-0844 1.8° (stock Ender-3 Z-axis motor)

* Other
  * [BLTouch Smart](https://www.antclabs.com/bltouch)
  * [300mm MGN12H linear rail on Y](https://www.amazon.com/Iverntech-Linear-Carriage-Printer-Machine/dp/B0762MPVN3/) w/([this mod](https://www.thingiverse.com/thing:2989134))
  * [Printed control box](https://www.thingiverse.com/thing:3398254)
  * [Raspberry Pi 3 Model B+](https://www.raspberrypi.org/products/raspberry-pi-3-model-b-plus/) running [OctoPrint](https://octoprint.org/) (SD card changes were to allow for remote firmware updates)
  * AC-powered bed:
    * [Custom-ordered Keenovo AC-powered silicone heater pad](https://keenovo.store/)
    * [OPTO 22 Z120D10 SSR](https://www.opto22.com/products/z120d10)
  * [Applied Magnets 2"x1/2"x1/8" N42SH High Temp Neodymium magnets](http://appliedmagnets.com/bar-magnets-2-in-x-1-2-in-x-1-8-in-high-temp-n42sh-neodymium-magnets-p-608.html) attached with [Permatex OPTIMUM GREY gasket maker](https://www.permatex.com/products/gasketing/optimum-gasket-makers/permatex-optimum-grey-gasket-maker/)
  * [Thekkiinngg textured PEI spring steel sheet](https://www.amazon.com/Thekkiinngg-Prusa-Double-Sided-Textured-Powder-Coated/dp/B07V1JYJS2/) (rotated 90 degrees)
  * [3 x Noctua NF-A4x10 40mm fans](https://noctua.at/en/nf-a4x10-flx) powered by [eBoot LM2596 DC buck converter](https://www.amazon.com/eBoot-LM2596-Converter-3-0-40V-1-5-35V/dp/B01GJ0SC2C)
  * [Mean Well LRS-350-24 Power Supply](https://www.meanwell.com/webapp/product/search.aspx?prod=LRS-350)
  * [X-axis tensioner](https://www.thingiverse.com/thing:3270228)

![Marlin 2.0.x, for 8-bit and 32-bit boards](https://i.imgur.com/JxbteZy.jpg)

### Stepper Motors

|BRAND|NAME/MODEL|SIZE|STEP_ANGLE|STEP/REV|V_DC|MAX_AMP|τ_HOLD|
|-----|----------|----|----------|--------|-------|-------|------|
|Usongshine|[17HS4023 42-23](https://ae01.alicdn.com/kf/HTB1dnr6emzqK1RjSZPcq6zTepXaB.jpg)|42x23|1.8°|200|4.1V|1.0A|13 Ncm|
|Creality|[JK42HS34-0844](https://ecksteinimg.de/Datasheet/Schrittmotor/JK42HS34-0844A/JK42HS34-0844YA-01.pdf)|42x34|1.8°|200|4.83V|1.0A|27 Ncm|
|Creality|[K42HS40-1004A-02F](https://www.reprap.me/creality-3d-two-phase-42-40-reprap-42mm-stepper-motor-for-ender-3-3d-printer.html)|42x40|1.8°|200|2.8V|1.5A|40 Ncm|
|Wetterot|[17HM3410](https://shop.watterott.com/Stepper-Motor-NEMA-17-400-Steps-42x34mm-2V-17A)|42x34|0.9°|400|2V|1.7A|24 Ncm|
