# Robotic Arm Hand

Open engineering project for an affordable, repairable, myoelectric prosthetic hand intended for a distal transradial / wrist-level user case.

## Project goal

The target is not a demonstration hand. The target is a **usable V1 prosthesis candidate** that can reliably perform a small set of high-value daily grasps while remaining light, serviceable, low-cost, and safe enough for supervised real-user evaluation.

Core V1 functions:

- power / cylindrical grip
- pinch grip
- tripod grip
- hook / carry grip
- fast intentional release
- proportional open/close from surface EMG
- current-limited grip force
- modular, replaceable fingers/tendons
- low-profile attachment strategy suitable for a long residual forearm
- manual mechanical release if the selected transmission can remain locked

## V1 baseline architecture — not frozen yet

The current baseline is **3 actuators**:

- independent index flexion
- grouped middle/ring/little flexion through an adaptive differential
- thumb flexion/opposition axis with a mechanically optimized thumb posture

Before the palm is frozen, this baseline will be bench-compared with a **2-actuator adaptive-synergy variant**. The independent-index actuator stays only if it provides enough measured pinch/tripod benefit to justify its mass, volume, energy and complexity.

Other baseline choices:

- tendon-driven, underactuated fingers
- passive elastic/spring extension
- 2-channel surface EMG for initial direct **velocity/rate** control
- physical grip-mode selector for predictable V1 use
- encoder + motor-current feedback
- sensor front end abstracted so FMG can be tested if sEMG stability is poor
- protected wearable battery system selected after actuator/energy-budget testing
- no powered wrist rotation in V1 when the user's physiological pronation/supination is adequate

The design deliberately prioritizes comfort, correct build length, predictable release, useful grasps, low mass and repairability over maximum dexterity.

## Case-specific hard constraint

Because this user appears to have a very long residual forearm / wrist-level limb, build height is a primary design variable. The distal wrist/adapter stack has a **<=25 mm development target**; <=15 mm is a stretch target if anatomy and mechanics allow it. Final symmetry is checked against the intact side.

See [`docs/DESIGN_REQUIREMENTS_V1.md`](docs/DESIGN_REQUIREMENTS_V1.md).

## Reference designs and current benchmarks

We are not copying a single project. The design is informed by:

- OpenBionics Prosthetic-Hands - adaptive differential / low actuator count
- SoftHand Pro - one-motor adaptive-synergy evidence and low-mass design
- Melbourne X-Limb - compact printed hand, embedded actuation, practical grasp set
- Tact Hand - affordable myoelectric prosthesis architecture
- ORTHOPUS MyoHand - thumb and open development lessons
- UJI-Hand MK4 - recent open student-team cable/underactuation lessons
- LibEMG / Hannes research - control and evaluation research
- current commercial benchmarks from TASKA, Open Bionics, PSYONIC, COVVI and Ottobock, including the 2026 speedhand/transcarpal fitting strategy

See [`docs/REFERENCE_PROJECTS.md`](docs/REFERENCE_PROJECTS.md) and [`docs/RED_TEAM_REVIEW_2026.md`](docs/RED_TEAM_REVIEW_2026.md).

## Repository map

- `docs/` - system architecture, requirements, roadmap, safety, human interface and research decisions
- `cad/` - future CAD source and manufacturing exports
- `electronics/` - schematics, PCB notes and wiring
- `firmware/` - embedded control software
- `bom/` - component selection and purchasing lists
- `tests/` - test protocols and results
- `data/` - data policy only; patient scans must not be committed to this public repository

## External-design provenance

Reference-project licenses differ. In particular, X-Limb is CC BY-NC 4.0 and OpenBionics Prosthetic-Hands is CC BY-SA 4.0. Do not copy external CAD/code into the core design without recording its license and obligations.

See [`docs/LICENSING_AND_PROVENANCE.md`](docs/LICENSING_AND_PROVENANCE.md).

## Privacy rule

**Do not commit patient photographs, 3D scans, medical history, EMG recordings, or identifying measurements to this public repository.** Store those in a private, access-controlled location and reference them by anonymous case ID only.

## Safety status

This is a research/student engineering project. It is **not a certified medical device**. Human fitting and use must proceed through appropriate clinical/prosthetics supervision, with staged bench validation and documented risk controls.

Jarvis may support geometry/test-data analysis later, but it must never be required for real-time control or safety of the worn V1 prosthesis.

## Start here

1. [`docs/DESIGN_REQUIREMENTS_V1.md`](docs/DESIGN_REQUIREMENTS_V1.md)
2. [`docs/ROADMAP.md`](docs/ROADMAP.md)
3. [`docs/RED_TEAM_REVIEW_2026.md`](docs/RED_TEAM_REVIEW_2026.md)
