# V1 Roadmap

This roadmap is ordered by **dependency and evidence**, not by calendar time.

## Stage 0 - Freeze the target

Define the user case as a distal transradial / wrist-level prosthesis until clinical examination confirms the exact level.

Outputs:

- residual-limb geometry and manual measurements
- intact-hand reference dimensions
- list of daily tasks the user actually wants
- maximum acceptable prosthesis length, mass and build envelope
- EMG feasibility notes
- clinical/prosthetics review plan

Gate: do not freeze wrist/socket geometry until the residual limb is medically stable.

## Stage 1 - Mechanical proof

Build one finger and one tendon path before building a complete hand.

Validate:

- joint geometry
- tendon travel
- return spring/elastic behavior
- friction and wear
- motor spool diameter
- tendon force vs fingertip force
- replaceability after damage

Then build the grouped three-finger differential and the independent index.

Gate: mechanism must grasp repeatably without tendon derailment, severe backlash, or unsafe pinch points.

## Stage 2 - Complete bench hand

Integrate palm, fingers, thumb, actuators and a temporary rigid fixture.

Target grasps:

- power
- pinch
- tripod
- hook/carry

The hand must work first from scripted commands before EMG is introduced.

Gate: repeatable grasping of representative daily objects with force limiting.

## Stage 3 - Embedded control

Add:

- MCU
- motor drivers
- encoder feedback
- current sensing
- watchdog
- hard disable / kill switch
- battery monitoring

Control hierarchy:

1. safety limits
2. motor current and position control
3. grasp state machine
4. user intent

Gate: faults must fail safe. A software crash must not leave the hand driving closed.

## Stage 4 - EMG direct control

Begin with two surface EMG channels.

Initial user interaction:

- flexor activation -> close / increase grip
- extensor activation -> open
- physical button -> select grip mode

Do not make machine learning a dependency for V1 usability.

Gate: the user can reliably open, close and hold the hand with repeatable calibration.

## Stage 5 - Human interface / socket prototype

Use the 3D scan and measurements to build the attachment geometry around the real residual limb.

Focus on:

- total prosthesis length
- suspension
- pressure distribution
- bony prominences
- skin-sensitive regions
- electrode repeatability
- don/doff
- cable routing
- serviceability

Gate: fitting must be comfortable enough for supervised sessions and must not create skin injury.

## Stage 6 - Wearable V1 integration

Integrate:

- final V1 hand
- socket/interface
- battery
- wiring
- protective covers
- EMG sensors

The system should remain modular so the hand, electronics and socket can be serviced separately.

## Stage 7 - Validation

Mechanical:

- repeated open/close cycles
- grip-force tests
- impact/finger overload tests
- tendon wear inspection
- screw-loosening inspection

Electrical:

- stall current
- thermal behavior
- battery protection
- brownout/restart behavior
- sensor disconnects

Human factors:

- comfort
- don/doff
- EMG repeatability
- command error rate
- object drops
- useful tasks

## Stage 8 - Environmental hardening

Only after the core hand is reliable:

- sweat management
- conformal coating
- gaskets and seals
- dust protection
- thermal testing
- splash/rain testing

Do not claim an IP rating without a defined and repeatable test.

## Stage 9 - Jarvis engineering workspace

Jarvis is not required to make V1 usable. It becomes an engineering accelerator later.

Planned workflow:

3D scan -> mesh cleanup -> patient digital twin -> CAD overlay -> measurements -> revision tracking -> test data -> design comparison.

Jarvis should treat geometry operations as deterministic tools, not as guessed model output.

See [`3D_SCAN_AND_JARVIS.md`](3D_SCAN_AND_JARVIS.md).

## Definition of a successful V1

V1 is successful when the user can, in supervised testing:

- put on and remove the system with manageable assistance
- intentionally open and close it from EMG
- hold common objects without crushing or frequent drops
- perform power, pinch, tripod and hook/carry tasks
- use it without unsafe heating or exposed electrical/mechanical hazards
- wear it without unacceptable pain or skin damage
- have a failed finger/tendon serviced without replacing the whole hand

V1 is not required to match a biological hand or a premium multi-articulating commercial prosthesis.