# Schematic review checklist

## General

* [x] CAD ERC 100% clean. If some errors are invalid due to toolchain quirks, each exception must be inspected and signed
off as invalid.
* [x] Verify pin numbers of all schematic symbols against datasheet or external interface specification document (if not yet board proven).
* [ ] Schematic symbol matches chosen component package
* [x] Verify pinning of all cables to other boards in the system (straight through vs mirror)

## Passive components
* [x] Power/voltage/tolerance ratings specified as required
* [ ] Ceramic capacitors appropriately de-rated for C/V curve
* [ ] Polarized components specified in schematic if using electrolytic caps etc

## Power supply

### System power input

* [x] Fusing and/or reverse voltage protection at system power inlet
* [ ] TVS at system power inlet
* [ ] Check total input capacitance and add inrush limiter if needed


### Decoupling
* [ ] Decoupling present for all ICs
* [ ] Decoupling meets/exceeds vendor recommendations if specified
* [ ] Bulk decoupling present at PSU

### General
* [x] All power inputs fed by correct voltage
* [x] Check high-power discrete semiconductors and passives to confirm they can handle expected load
* [ ] Analog rails filtered/isolated from digital circuitry as needed

### Errata
* [x] Read errata sheets (if available) for all major devices
* [x] STM32: do not use JTRST pin as an I/O

## Signals

### Digital

* [x] Signals are correct logic level for input pin
* [x] Pullups on all open-drain outputs
* [x] Termination on all high-speed signals
* [x] TX/RX paired correctly for UART, SPI, MGT, etc
* [x] Active high/low enable signal polarity correct

### Strap/init pins
* [x] Pullup/pulldowns on all signals that need defined state at boot -> TODO in Software
* [x] JTAG/ICSP connector provided for all programmable devices

### External interface protection

* [x] Power outputs (USB etc) current limited
* [ ] ESD protection on data lines going off board -> flemme

### Debugging / reworkability

* [ ] Use 0-ohm resistors vs direct hard-wiring for strap pins when possible
* [x] Provide multiple ground clips/points for scope probes
* [x] Dedicated ground in close proximity to analog test points
* [x] Test points on all power rails
* [x] Test points on interesting signals which may need probing for bringup/debug
