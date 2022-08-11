# Schematic review checklist

## General

* [x] CAD ERC 100% clean. If some errors are invalid due to toolchain quirks, each exception must be inspected and signed
off as invalid.
* [ ] Verify pin numbers of all schematic symbols against datasheet or external interface specification document (if not yet board proven).
* [ ] Schematic symbol matches chosen component package
* [ ] Thermal pads are connected to correct power rail (may not always be ground)
* [ ] Debug interfaces are not power gated in sleep mode

## Passive components
* [ ] Power/voltage/tolerance ratings specified as required
* [ ] Ceramic capacitors appropriately de-rated for C/V curve
* [ ] Polarized components specified in schematic if using electrolytic caps etc

## Power supply

### System power input

* [ ] Fusing and/or reverse voltage protection at system power inlet
* [ ] Check total input capacitance and add inrush limiter if needed

### Regulators

* [ ] Under/overvoltage protection configured correctly if used
* [ ] Verify estimated power usage per rail against regulator rating
* [ ] Current-sense resistors on power rails after regulator output caps, not in switching loop
* [ ] Remote sense used on low voltage or high current rails
* [ ] Linear regulators and voltage reference ICs are stable with selected output cap ESR
* [ ] Confirm power rail sequencing against device datasheets

### Decoupling
* [ ] Decoupling present for all ICs
* [ ] Decoupling meets/exceeds vendor recommendations if specified
* [ ] Bulk decoupling present at PSU

### General
* [ ] All power inputs fed by correct voltage
* [ ] Check high-power discrete semiconductors and passives to confirm they can handle expected load
* [ ] Analog rails filtered/isolated from digital circuitry as needed

## Signals

### Digital

* [ ] Signals are correct logic level for input pin
* [ ] Pullups on all open-drain outputs
* [ ] Pulldowns on all PECL outputs
* [ ] Termination on all high-speed signals
* [ ] AC coupling caps on gigabit transceivers
* [ ] TX/RX paired correctly for UART, SPI, MGT, etc
* [ ] Differential pair polarity / pairing correct
* [ ] Active high/low enable signal polarity correct
* [ ] I/O banking rules met on FPGAs etc
* [ ] When using auto-sensing level shifters, ensure the intended receiver doesn't have a pullup/down

### Analog

* [ ] RC time constant for attenuators sane given ADC sampling frequency
* [ ] Verify frequency response of RF components across entire operating range. Don't assume a "1-100 MHz" amplifier has the
same gain across the whole range.
* [ ] Verify polarity of op-amp feedback

### Clocks

* [ ] All oscillators meet required jitter / frequency tolerance. Be extra cautious with MEMS oscillators as these tend to have higher jitter.
* [ ] Correct load caps provided for discrete crystals
* [ ] Crystals only used if IC has an integrated crystal driver
* [ ] Banking / clock capable input rules met for clocks going to FPGAs
    * [ ] Xilinx FPGAs: single ended clocks use _P half of differential pairs
    * [ ] If possible, create dummy design with all clocks and other key signals and verify it P&R's properly

### Strap/init pins
* [ ] Pullup/pulldowns on all signals that need defined state at boot
* [ ] Strap pins connected to correct rail for desired state
* [ ] JTAG/ICSP connector provided for all programmable devices
* [ ] Config/boot flash provided for all FPGAs or MPUs without internal flash
* [ ] Reference resistors correct value and reference rail

### External interface protection

* [ ] Power outputs (USB etc) current limited
* [ ] ESD protection on data lines going off board

### Debugging / reworkability

* [ ] Use 0-ohm resistors vs direct hard-wiring for strap pins when possible
* [ ] Provide multiple ground clips/points for scope probes
* [ ] Dedicated ground in close proximity to analog test points
* [ ] Test points on all power rails
* [ ] Test points on interesting signals which may need probing for bringup/debug

## Thermal

* [ ] Power estimates for all large / high power ICs
* [ ] Thermal calculations for all large / high power ICs
* [ ] Specify heatsinks as needed

