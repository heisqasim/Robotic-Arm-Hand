# Mechanical Concept

## V1 architecture status

The hand remains tendon-driven and underactuated, but the actuator count is no longer treated as frozen.

### Baseline A — three actuator groups

```text
Thumb  <--- actuator C

Index  <--- actuator A

Middle ----\
Ring   -----+--- adaptive differential <--- actuator B
Little ----/
```

### Variant B — two actuator groups

```text
Index  -----\
Middle ------\
Ring   -------+--- adaptive synergy / differential <--- actuator A
Little ------/

Thumb  <--- actuator B
```

Variant B is not automatically better. The purpose of the experiment is to learn whether independent index control is worth the additional distal mass, packaging volume, power and failure points.

The palm is not frozen until the two layouts are compared on pinch/tripod repeatability, power grasp, opening width, weight, current and service complexity.

## Finger module

Each finger should be independently replaceable.

Proposed construction:

- rigid phalange segments
- pinned MCP/PIP joints (and DIP if the selected geometry requires it)
- high-strength tendon for flexion
- spring/elastic return for extension
- soft/high-friction fingertip pad
- mechanical travel stops
- replaceable or resettable overload/compliance feature at vulnerable joints

Avoid making the entire finger a single fatigue-critical flexure for the daily-use candidate.

## Overload and impact strategy

A repairable finger is useful, but a daily-use hand should also avoid transmitting every accidental impact directly into the gearbox.

Bench-test at least one of:

- spring-loaded / compliant joint element
- breakaway/resettable joint feature
- sacrificial inexpensive link
- series-elastic tendon segment

The desired failure order is:

```text
safe compliance / resettable release
    before
cheap replaceable sacrificial part
    before
printed phalanx damage
    before
gearbox / motor / palm damage
```

Open Bionics Hero RGD, TASKA and PSYONIC provide commercial evidence that impact tolerance/compliance deserves first-class design attention.

## Tendon system

Preferred tendon characteristics:

- high tensile strength
- low stretch in the primary load path
- small diameter
- abrasion resistant
- easy local replacement

Dyneema/Spectra-class braided line remains a strong candidate for development.

Tendon routing must minimize:

- sharp bends
- rubbing against printed edges
- lateral derailment from pulleys/spools
- sudden radius changes
- impossible service access

Use replaceable guides/bushings where wear is expected rather than allowing the tendon to cut directly into expensive structural parts.

## Differential / synergy

For grouped fingers, use an adaptive differential/whiffletree or equivalent mechanism so early object contact in one finger does not force the others to stop.

Purpose:

- first-contact finger can stop
- remaining fingers continue closing
- grasp conforms to irregular objects
- actuator count remains low

A four-finger synergy version is part of the two-actuator architecture experiment.

## Series elasticity experiment

Recent underactuated prosthetic-hand research shows useful benefits from series elasticity: impact isolation, contact/force inference, impedance behavior and safer interaction. It also creates real costs: extra friction, calibration, bulk and sensing requirements.

Therefore series elasticity is an **experiment**, not a default requirement.

Measure whether an elastic element can provide:

- repeatable tendon-force estimate from deflection
- earlier contact detection than motor current alone
- lower peak impact loads
- acceptable hysteresis and friction

Remove it if the added complexity is not justified.

## Thumb

Thumb geometry remains the highest-priority mechanical experiment after the finger module.

V1 needs:

- opposition for power/pinch/tripod
- enough clearance for bottles/cups
- useful lateral/key contact if achievable simply
- safe release path

A manually indexed thumb-abduction/pre-position setting is acceptable if it materially reduces weight and failure risk. Powered thumb rotation is not automatically required.

## Wrist / distal adapter

This user case has almost no spare anatomical build length.

Design target:

- <=25 mm distal adapter build height
- <=15 mm stretch target if anatomy/mechanics allow
- use preserved forearm pronation/supination when clinically/functionally adequate
- do not add powered wrist rotation to V1 without evidence that the user needs it

The adapter must be structurally testable and separately serviceable from both socket and hand.

## Holding-power strategy

A hand that holds a cup by keeping a motor near stall wastes energy and creates heat.

During the bench phase measure electrical power while maintaining representative grasps.

If holding power is excessive, evaluate:

- self-locking gear ratio/transmission
- passive brake
- mechanical tendon latch

Any design that can stay mechanically closed after power loss requires a **manual emergency release** that the user or helper can operate without software.

## Palm

The palm must package only what earns its volume:

- selected two- or three-actuator arrangement
- tendon spools/differential
- serviceable tendon paths
- controller/driver or wiring channels as packaging permits
- optional contact-sensor pockets at thumb/index
- protective dry electronics zone
- dorsal service access

For this long-residual-limb case, do not create a long wrist motor cluster.

## Material strategy

### Fast geometry prototypes

- PLA/PETG for fit checks, fixtures and short bench experiments

### Functional prototypes

- ASA or nylon where appropriate
- metal pins/fasteners at repeated bearing/wear interfaces

### Daily-use candidate

- **tough unfilled PA12/nylon as the default printed structural candidate**, especially where impact toughness matters
- PA12-CF / other filled nylon selectively where extra stiffness is specifically required and brittleness/anisotropy is acceptable
- TPU or silicone for grip and impact surfaces
- stainless steel for pins/fasteners exposed to sweat
- aluminium or POM for selected wear/high-load features when beneficial

Commercial PA12 hands show that “stronger-looking carbon-filled material everywhere” is not automatically the best solution. Toughness, impact behavior, print process and repairability matter as much as nominal stiffness.

## Mechanical acceptance evidence

Before wearable integration:

- >=10,000 bench cycles on the selected mechanism
- repeatable opening/closing
- stable tendon tracking
- measured grip force
- open-to-close time measurement
- controlled stalls
- holding-power measurement
- impact/overload testing
- manual release demonstration after power removal if transmission can lock
- replaceable tendon/finger service demonstration
- no exposed pinch or sharp-edge hazard

Before extended supervised daily-use evaluation, target >=100,000 full-hand cycles. The longer development target is 250,000 cycles.