# Mechanical Concept

## Selected V1 concept

The V1 hand uses three actuator groups:

```text
Thumb  <--- actuator C

Index  <--- actuator A

Middle ----\
Ring   -----+--- adaptive differential <--- actuator B
Little ----/
```

The purpose is to keep the actuator count low while preserving the two grasp relationships that matter most: thumb-to-index precision and adaptive wrapping of the remaining fingers.

## Finger module

Each finger should be independently replaceable.

Proposed construction:

- rigid phalange segments
- pinned MCP/PIP joints (and DIP if the selected geometry requires it)
- high-strength tendon for flexion
- spring/elastic return for extension
- soft/high-friction fingertip pad
- mechanical travel stops

Avoid making the entire finger a single fatigue-critical flexure for the daily-use candidate.

## Tendon system

Preferred tendon characteristics:

- high tensile strength
- low stretch
- small diameter
- abrasion resistant
- easy local replacement

Dyneema/Spectra-class braided line is a strong candidate for development.

Tendon routing must be designed to minimize:

- sharp bends
- rubbing against printed edges
- lateral derailment from pulleys/spools
- sudden radius changes

## Differential

The three-finger group should use a whiffletree/adaptive differential inspired by OpenBionics rather than forcing all three fingers to identical angles.

Purpose:

- first finger that contacts an object can stop
- remaining fingers continue closing
- the hand conforms around irregular objects with one actuator

## Thumb

Thumb geometry is the highest-priority mechanical experiment after the finger module.

V1 target positions:

- opposition for power/pinch/tripod
- enough clearance for opening around bottles/cups

A manually indexed thumb-abduction setting is acceptable for early V1 if it materially reduces weight and failure risk. Powered thumb rotation is a later upgrade unless bench tests show it is essential.

## Palm

The palm must package:

- three actuators or actuator/gear assemblies
- tendon spools
- differential
- motor drivers / wiring channels
- service access

For this long-residual-limb case, do not place a large motor cluster in a long wrist extension.

## Material strategy

Prototype iterations:

- PLA/PETG only for geometry checks and fixtures
- ASA/nylon for functional printed parts where available

Daily-use candidate:

- PA12 / PA12-CF or equivalent tough engineering polymer for structural printed parts
- TPU or silicone for grip surfaces/covers
- stainless steel for pins/fasteners exposed to sweat
- aluminium or POM for selected high-load or wear-critical parts when beneficial

Material choice does not replace cycle testing.

## Mechanical acceptance evidence

Before wearable integration the hand should demonstrate:

- repeatable opening and closing
- stable tendon tracking
- measured grip force
- controlled stalls
- replaceable tendon/finger service
- no exposed pinch or sharp-edge hazard
- no gross structural damage during repeated cycle testing