# Schematic review checklist

## General

* CAD ERC 100% clean. If some errors are invalid due to toolchain quirks, each exception must be inspected and signed
off as invalid.
* Verify pin numbers of all schematic symbols against datasheet (if not yet board proven).
* Schematic symbol matches chosen component package
* Thermal pads are connected to correct power rail (may not always be ground)
* Debug interfaces are not power gated in sleep mode

## Passive components
* Power/voltage/tolerance ratings specified as required
* Ceramic capacitors appropriately de-rated for C/V curve
* Polarized components specified in schematic if using electrolytic caps etc

## Power supply

### System power input

* Fusing and/or reverse voltage protection at system power inlet
* Check total input capacitance and add inrush limiter if needed

### Regulators

* Under/overvoltage protection configured correctly if used
* Verify estimated power usage per rail against regulator rating
* Current-sense resistors on power rails after regulator output caps, not in switching loop
* Remote sense used on low voltage or high current rails
* Linear regulators are stable with selected output cap ESR

### Decoupling
* Decoupling present for all ICs
* Decoupling meets/exceeds vendor recommendations if specified
* Bulk decoupling present at PSU

### General
* All power inputs fed by correct voltage
* Check high-power discrete semiconductors and passives to confirm they can handle expected load
* Analog rails filtered/isolated from digital circuitry as needed
