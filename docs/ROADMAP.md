# V1 Roadmap

This roadmap is ordered by **dependency and evidence**, not by calendar time.

## Stage 0 - Freeze the user constraints, not the mechanism

Treat the current case as distal transradial / wrist-level until clinical examination confirms the exact level.

Outputs:

- residual-limb geometry and manual measurements
- intact-hand/forearm reference dimensions
- list of daily tasks the user actually wants
- physiological pronation/supination assessment
- maximum acceptable prosthesis length, mass and build envelope
- distal adapter target: <=25 mm, with <=15 mm as a stretch goal if anatomy/mechanics permit
- EMG feasibility notes and candidate sites
- scar/bony/sensitive-skin map
- sweat/ventilation considerations
- clinical/prosthetics review plan

Gate: do not freeze wrist/socket geometry until the residual limb is medically stable. Do not add powered wrist rotation to V1 if preserved biological rotation already provides the function.

## Stage 1 - Finger proof + architecture bake-off

Build one finger and one tendon path before building a complete hand.

Validate:

- joint geometry
- tendon travel
- return spring/elastic behavior
- friction and wear
- motor spool diameter
- tendon force vs fingertip force
- impact/overload behavior
- replaceability after damage
- optional series-elastic element / tendon-deflection experiment

Then compare two actuator layouts using the same basic finger geometry:

### Variant A — 3 actuators

- index independent
- middle/ring/little adaptive differential
- thumb independent

### Variant B — 2 actuators

- four-finger adaptive synergy/differential
- thumb independent or mechanically pre-positioned during the experiment

Measure:

- power-grasp quality
- pinch/tripod repeatability
- opening width
- mass and palm volume
- current/energy use
- holding-power requirement
- failure/service complexity

Gate: keep the independent-index actuator only if its measured utility justifies the extra mass, volume, energy and complexity.

## Stage 2 - Complete bench hand

Integrate palm, fingers, thumb, selected actuator layout and a temporary rigid fixture.

Target grasps:

- power / cylindrical
- pinch
- tripod
- hook/carry
- lateral/key pinch if the chosen thumb geometry supports it without large complexity

The hand must work first from scripted commands before EMG is introduced.

Design requirements:

- no normal grasp should depend on sustained near-stall current
- investigate self-locking transmission, brake or latch only if needed for efficient hold
- if the mechanism can remain locked, add a **manual mechanical emergency release**
- add replaceable/resettable overload protection where finger/gearbox impact risk is high
- make thumb/index geometry sensor-ready for later pressure/contact sensors

Gate: repeatable grasp and release of representative daily objects with force limiting and safe fault release.

## Stage 3 - Embedded control

Add:

- MCU
- motor drivers
- encoder feedback
- current sensing
- watchdog
- hard electrical disable / kill switch
- manual mechanical release if required by transmission
- battery monitoring
- temperature monitoring where heating risk exists

Control hierarchy:

1. hard/mechanical safety limits
2. current, travel and thermal limits
3. motor velocity/position control
4. grasp state machine
5. user intent

Gate: faults fail safe. A software crash, sensor disconnect or low battery must not leave the hand actively driving closed or make release impossible.

## Stage 4 - Intent sensing and direct control

### Baseline: 2-channel sEMG

Initial interaction:

- flexor-dominant activation -> proportional closing **velocity/rate**
- extensor-dominant activation -> proportional opening velocity/rate
- physical button -> select grip mode

Add:

- calibration after donning
- deadband/hysteresis
- signal quality check
- tests across arm position, repeated don/doff, sweat and fatigue

### Fallback path

Keep the control interface abstracted so a low-cost **force-myography (FMG)** array can be tested if sEMG proves unstable for this user. HD-EMG, sonomyography and other deformation-based interfaces are later research, not V1 dependencies.

Gate: the user can intentionally open, close, hold and release with repeatable calibration and an acceptably low false-activation rate.

## Stage 5 - Human interface / socket prototype

Use the 3D scan and manual measurements to build the attachment around the actual residual limb.

Focus on:

- total prosthesis length and alignment against intact side
- suspension and anti-rotation
- pressure distribution
- bony prominences / scars / sensitive areas
- repeatable electrode contact after don/doff
- **ventilation, sweat paths and moisture management**
- cable/electrode strain relief
- low-profile distal adapter
- easy don/doff
- service access
- dry/wet zone separation where practical

Use test sockets/partial shells before committing to the final material.

Gate: supervised fitting is stable and comfortable, with no concerning skin response and with control signals remaining usable after repeated don/doff.

## Stage 6 - Wearable V1 integration

Integrate:

- selected hand architecture
- socket/interface
- battery
- wiring
- protective covers
- EMG interface
- manual release
- early sealing features already designed into the CAD (gasket grooves, cable seals, protected electronics zone)

The hand, electronics, battery and socket should remain separately serviceable.

## Stage 7 - Quantitative validation

### Mechanical gates

- >=10,000 cycles before wearable integration
- >=100,000 full-hand cycles before extended supervised daily-use evaluation
- 250,000-cycle development target
- grip-force tests by grasp type
- blocked-finger / adaptive-differential tests
- finger overload and impact tests
- tendon/pulley wear inspection
- screw-loosening inspection
- structural adapter retention

Development targets:

- power grip >=30 N baseline; >=50 N stretch
- pinch >=10–15 N baseline; >=20 N stretch
- open-to-close <=1.0 s target

### Electrical/control tests

- motor stall
- encoder loss
- EMG disconnect/noise
- MCU reset while gripping
- brownout
- low-battery behavior
- stuck command
- driver/motor heating
- manual release after power loss
- false activation and re-don calibration repeatability

### Human-factor/function tests

- comfort and skin checks
- suspension/rotation under load
- don/doff time and repeatability
- calibration time
- command error / false activation rate
- release time and failed-release count
- object-drop count
- fixed daily-object task battery
- targeted Box and Block Test (tBBT) or standard BBT when appropriate

## Stage 8 - Environmental qualification

Environmental *features* begin earlier, but formal hardening/testing follows core reliability.

Validate:

- sweat exposure and cleanup
- corrosion resistance
- conformal coating where appropriate
- gasket/cable-seal performance
- dust exposure
- thermal exposure
- splash/rain tests

Do not claim an IP rating without a defined, repeatable test.

## Stage 9 - Jarvis engineering workspace

Jarvis is not required to make V1 usable. It becomes an engineering accelerator later.

Planned workflow:

3D scan -> mesh cleanup -> anonymous digital twin -> CAD overlay -> measurements -> revision tracking -> test data -> design comparison.

Jarvis should treat geometry operations as deterministic tools, not guessed model output.

**Jarvis must never sit in the real-time actuator/safety path of the worn V1 prosthesis.** Embedded safety and basic operation remain local and deterministic.

See [`3D_SCAN_AND_JARVIS.md`](3D_SCAN_AND_JARVIS.md).

## Definition of a successful V1

V1 is successful when the user can, in supervised testing:

- don and remove the system with manageable assistance
- intentionally open, close, hold and rapidly release from the selected intent interface
- hold common objects without crushing or frequent drops
- perform power, pinch, tripod and hook/carry tasks
- use it without unsafe heating or exposed electrical/mechanical hazards
- wear it without unacceptable pain or skin damage
- retain usable control after repeated don/doff and realistic sweat/posture variation
- manually release the hand after an electrical/control failure if the transmission can lock
- have a failed finger/tendon serviced without replacing the whole hand

V1 is not required to match a biological hand or a premium multi-articulating commercial prosthesis.

Read [`DESIGN_REQUIREMENTS_V1.md`](DESIGN_REQUIREMENTS_V1.md) for the current measurable targets and [`RED_TEAM_REVIEW_2026.md`](RED_TEAM_REVIEW_2026.md) for the evidence behind the changes.