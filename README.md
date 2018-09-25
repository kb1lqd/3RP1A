# 3RP1A

This is a project to drive a 3RP1A electrostatic deflection cathode ray tube that I have laying around. The intention is to design and build the power circuitry, amplifier(s), and a video source such as a micro-controller to create a functional art piece such as a clock. This is a learning project for me.

# Electrostatic CRT Tube Components


## Electron Gun

 * **Cathode (Negative potential)**
   * Source of electrons
   * 3RP1A is a "Hot Cathode" (must be heated for electron flow due to [thermionic emission](https://en.wikipedia.org/wiki/Thermionic_emission))
 * **Anode (Positively charged)**
   * Attracts electrons from cathode
 * **Heater filament**
   * Indirectly heats the cathode allowing electrons to flow through vacuum
 * **Control Grid(s)**
   * Regulate the amount of electrons allowed to pass through to the phosphor screen (i.e. the "brightness" of the electron beam)
   * Also provides a first electron "Lens"

## Beam Deflection

 * **Focusing Anode**
   * A medium voltage anode that forms an   electrostatic field between the high voltage accelerating anode
   * The strength of the field between the two anodes is used an an electron lens to direct the electrons from a diverging to converging beam focused at the distance of the viewing screen.
 * **Deflection Plates**
   * Two plates positioned with the electron beam between them that deflect the beam using varying potential between the plates to pull the beam toward one plate or the other.
   * There are two deflection plates oriented to provide both Horizontal and Vertical deflection.

# High Voltage Supply

I'd like to design a simple DC/DC flyback converter for this application. This seems both interesting and more than adequate for the application. I can tap off using large variable resistors voltages to tune the focus and brightness grid plates. The deflection plates can use this high voltage rail to differentially tune the beam deflection.

Using the 3RP1A datasheet it looks like the maximum anode voltage will be between 500V-4kV. A nominal range looks to be about 1.5kV. This will likely need a transformer with a 1:100 to 1:300 turns ratio having not yet done the math.

## Transformer Suppliers

I'll need a high turns ratio transformer and would prefer to buy a new used or otherwise somewhat known transformer from a vendor.

* https://www.amazing1.com/transformers-high-voltage-high-frequency.html
* http://magnetic-components.mpsind.com/viewitems/flyback-transformers/p3800-series-isolated-flyback-transformers

## Flyback Converter

It seems that many high voltage projects use unregulated flyback converter designs implementing a simple open-loop switching waveform into the transformer. This alleviates design complexity for both regulation and isolation. It should be possible to use easily a primary-side flyback converter IC as a turns ration up or down shouldn't matter. Primary side sensing avoids the high-voltage sensing issues and isolation. The LT3748 may be a good candidate.

* http://www.analog.com/en/products/lt3748.html

I am a bit concerned about how to get loop compensation correct. I might have to math this one and cross my fingers for no smoke :|

# Concerns

* High Voltage
 * Work carefully
 * Provide discharge paths to avoid dangerous charge storage
 * Be mindful of voltage arcing and creepage on the PCB
* X-Rays from CRT's
 * Initial research indicates that CRT XRAY danger is low below ~15KV.
 * The 3RP1A operates below ~4KV


# References

## Datasheets

* [RCA](http://electronbin.com/sheets/049/3/3RP1A.pdf)
* [DuMont](http://electronbin.com/sheets/041/3/3RP1A.pdf)
* [Frank POCNET - 3PR1A](https://frank.pocnet.net/sheets/168/3/3RP1.pdf|)

## High Voltage Supplies

* [Linear Technologies -  AN65](http://www.analog.com/media/en/technical-documentation/application-notes/an65fa.pdf)


## Electrostatic CRT Opeartion

* [Electrostatic CRT components/functions](http://www.tpub.com/neets/book6/21e.htm)
