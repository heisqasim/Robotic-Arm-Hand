# Robotic Arm Hand

Open engineering project for an affordable, repairable, myoelectric prosthetic hand intended for a distal transradial / wrist-level user case.

## Project goal

The target is not a demonstration hand. The target is a **usable V1 prosthesis candidate** that can reliably perform a small set of high-value daily grasps while remaining light, serviceable, low-cost, and safe enough for supervised real-user evaluation.

Core V1 functions:

- power grip
- pinch grip
- tripod grip
- hook / carry grip
- proportional open/close from surface EMG
- current-limited grip force
- modular, replaceable fingers
- low-profile attachment strategy suitable for a long residual forearm

## Chosen V1 architecture

- **3 actuators**
  - independent index flexion
  - grouped middle/ring/little flexion through an adaptive differential
  - thumb flexion/opposition axis with a mechanically optimized thumb posture
- tendon-driven, underactuated fingers
- passive elastic/spring extension
- 2-channel surface EMG for initial direct control
- physical grip-mode selector for predictable use
- encoder + motor-current feedback
- protected 2S battery system for wearable prototypes

This architecture deliberately prioritizes reliability and the most useful grasps over maximum dexterity.

## Reference designs

We are not copying a single project. The design is informed by:

- OpenBionics Prosthetic-Hands - adaptive differential / low actuator count
- Melbourne X-Limb - compact printed hand, embedded actuation, practical grasp set
- Tact Hand - affordable myoelectric prosthesis architecture
- ORTHOPUS MyoHand - thumb and open development lessons
- LibEMG - EMG research and evaluation tooling
- commercial benchmarks from TASKA, Open Bionics, PSYONIC, COVVI and Ottobock

See [`docs/REFERENCE_PROJECTS.md`](docs/REFERENCE_PROJECTS.md).

## Repository map

- `docs/` - system architecture, roadmap, safety, human interface and research decisions
- `cad/` - future CAD source and manufacturing exports
- `electronics/` - schematics, PCB notes and wiring
- `firmware/` - embedded control software
- `bom/` - component selection and purchasing lists
- `tests/` - test protocols and results
- `data/` - data policy only; patient scans must not be committed to this public repository

## Privacy rule

**Do not commit patient photographs, 3D scans, medical history, EMG recordings, or identifying measurements to this public repository.** Store those in a private, access-controlled location and reference them by anonymous case ID only.

## Safety status

This is a research/student engineering project. It is **not a certified medical device**. Human fitting and use must proceed through appropriate clinical/prosthetics supervision, with staged bench validation and documented risk controls.

## Main roadmap

Read [`docs/ROADMAP.md`](docs/ROADMAP.md) first.