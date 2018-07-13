# Layout review checklist

## General

* [Schematic review](schematic-checklist.md) complete and signed off, including pin swaps done during layout
* Layout DRC 100% clean

## Decoupling

* Decoupling caps as close to power pins as possible
* Low inductance mounting used for decoupling (prefer ViP if available, otherwise "[]8" shaped side vias

## DFM / yield enhancement

* All design rules within manufacturer's capability
* Minimize use of vias/traces that push fab limits
* Controlled impedance specified in fab notes if applicable
* Stackup verified with manufacturer and specified in fab notes
* Board finish specified in fab notes
* If panelizing, add panel location indicators for identifying location-specific reflow issues
* (recommended) Layer number markers specified to ensure correct assembly
* Fiducials present (on both sides of board) if targeting automated assembly
* Fiducial pattern asymmetric to detect rotated boards
* Soldermask/copper clearance on fiducials respected
* Panelization specified if required

## Footprints

* Confirm components are available in the selected package
* Verify schematic symbol matches the selected package
* Confirm pinout diagram is from top vs bottom of package
* (recommended) PCB printed 1:1 on paper and checked against physical parts
* 3D models obtained (if available) and checked against footprints
* Soldermask apertures on all SMT lands and PTH pads

## Differential pairs
* Routed differentially
* Skew matched
* Correct clearance to non-coupled nets

## High-speed signals

* Sufficient clearance to potential aggressors
* Length matched if required
* Minimize crossing reference plane splits/slots or changing layers, use caps/stitching vias if unavoidable
* Confirm fab can do copper to edge of PCB for edge launch connectors
* Double-check pad width on connectors and add plane cutouts if needed to minimize impedance discontinuities

## Power
* Minimal slots in planes from via antipads
* Sufficient width for planes/traces for required current

## Sensitive analog
* Guard ring / EMI cages provided if needed
* Physically separated from high current SMPS or other noise sources
* Consider microphone effect on MLCCs if near strong sound sources

## Mechanical
* LEDs, buttons, and other UI elements on outward-facing side of board
* Keep-outs around PCB perimeter, card guides, panelization mouse-bites, etc respected
* Stress-sensitive components (MLCC) sufficiently clear from V-score or mouse bite locations, and oriented to reduce
bending stress
* Clearance around large ICs for heatsinks/fans if required
* Clearance around pluggable connectors for mating cable/connector
* Clearance around mounting holes for screws
* Plane keepouts and clearance provided for shielded connectors, magnetics, etc
* Confirm PCB dimensions and mounting hole size/placement against enclosure or card rack design
* Verify mounting hole connection/isolation
* Components not physically overlapping/colliding
* Clearance provided around solder-in test points for probe tips

## Thermal
