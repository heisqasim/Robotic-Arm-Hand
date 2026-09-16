# V1 Design Requirements

These are engineering requirements and development gates for the research V1. They are not medical claims, certification limits, or permission for unsupervised use.

## 1. User-case constraints

- The current case is treated as **wrist-level / very distal transradial** until clinically confirmed.
- Final geometry is patient-specific; intact-side dimensions and residual-limb measurements control length and scale.
- Preserve physiological pronation/supination when usable rather than adding powered wrist rotation to V1.
- Distal wrist/adapter build height: **<=25 mm target**, with **<=15 mm stretch target** if the actual anatomy and mechanical stack permit it.
- The socket, adapter and hand stack must be checked against intact-side length before palm geometry is frozen.

## 2. Functional scope

V1 must support repeatable:

- power / cylindrical grasp
- pinch
- tripod
- hook / carry
- rapid intentional release

Lateral/key pinch is desirable if the chosen thumb geometry provides it without excessive complexity.

## 3. Actuation architecture gate

The current three-actuator design is the **baseline**, not a fixed requirement.

Before the palm is frozen, compare:

### Variant A — three actuators

- independent index
- middle/ring/little adaptive differential
- independent thumb

### Variant B — two actuators

- four-finger adaptive synergy/differential
- independent thumb or mechanically pre-positioned thumb during the experiment

The independent-index actuator is retained only if measured pinch/tripod performance justifies its mass, packaging volume, current draw, wiring and service complexity.

## 4. Mechanical targets

- Hand-module mass: **<=350 g target**; mandatory architecture review above 400 g.
- Full wearable system: **<=600 g development target** if feasible for this case.
- Full open-to-close time: **<=1.0 s target**.
- Power grip: **>=30 N baseline**, >=50 N stretch.
- Pinch: **>=10–15 N baseline**, >=20 N stretch.
- Stable tendon tracking through full travel and blocked-finger tests.
- Each finger/tendon must be serviceable without remaking the full hand.
- No exposed sharp edge or avoidable pinch/shear hazard.
- Mechanical overload protection must be investigated at vulnerable finger/joint locations.
- Hold-power consumption must be measured; normal object holding must not depend on sustained near-stall current.
- If a self-locking gearbox, brake or latch is used, a **manual mechanical emergency release** is mandatory.

## 5. Durability development gates

These are project gates, not claims of lifetime:

- >=10,000 cycles: mechanism/bench gate before wearable integration
- >=100,000 full-hand cycles: gate before extended supervised daily-use evaluation
- 250,000 cycles: development durability target

Inspect at defined intervals for:

- tendon abrasion/elongation
- pulley/spool wear
- joint/pin wear
- screw loosening
- printed-part cracking
- gearbox backlash/noise
- loss of grip force

## 6. Human-control interface

### V1 baseline

- 2-channel surface EMG
- agonist/antagonist muscle pair selected on the real user
- proportional **velocity/rate** control for open/close
- deterministic physical grip-mode selector for initial V1
- brief calibration after donning
- hysteresis/deadband and activation thresholds

### Sensor abstraction

Firmware must separate intent sensing from grasp/motor safety so the front end can later be replaced or supplemented.

Research fallback order:

1. two-channel sEMG — V1 baseline
2. force myography (FMG) array — low-cost fallback experiment if sEMG stability is unacceptable
3. additional/HD-EMG — later research
4. sonomyography/MMG/other deformation sensing — later research

## 7. Control safety

Safety limits must remain below and independent from intent decoding.

Mandatory behaviors:

- current limit for each motor
- mechanical/electrical travel limit
- motion timeout
- watchdog
- brownout/restart handling
- hard electrical disable
- manual mechanical release if the transmission can stay locked
- safe response to encoder, EMG and sensor disconnects where detectable
- no live dependency on phone, cloud, Jarvis or a high-level AI service

## 8. Sensing and feedback

Baseline:

- encoder/position feedback where available
- motor-current measurement for contact/stall/fault inference

Design the thumb/index CAD to be **sensor-ready** for optional pressure/contact sensing even if the sensors are not populated in the first build.

Series elasticity / tendon-deflection sensing is a bench experiment, not a mandatory architecture feature, and is kept only if it improves impact tolerance/contact estimation without unacceptable friction, bulk or calibration burden.

## 9. Socket and skin interface

The fitted interface must address from the first prototype:

- suspension and anti-rotation
- pressure relief over sensitive/bony/scar areas
- electrode placement repeatability
- ventilation and sweat paths
- don/doff repeatability
- cable/wire strain relief
- service access
- protection from sharp internal transitions

A 3D scan supplies geometry only. Pressure-bearing decisions require clinical/prosthetics input.

## 10. Environmental design

- Sweat resistance is an early design requirement.
- Separate wet/skin-facing zones from protected electronics where practical.
- Add gasket grooves, cable-seal strategy and drainage/ventilation features during CAD, not as a late retrofit.
- Do not claim IP rating before repeatable ingress testing.
- Use corrosion-resistant fasteners/materials near sweat exposure.

## 11. Materials

Prototype geometry may use PLA/PETG.

Functional prototypes and the daily-use candidate should prioritize toughness and repeatability:

- tough PA12/nylon as default structural printed material where practical
- PA12-CF or other filled nylon selectively where stiffness is specifically needed
- TPU/silicone for grip/impact interfaces
- stainless steel pins/fasteners for sweat/wear regions
- aluminium/POM/other engineered parts where a printed bearing or high-load feature is inadequate

Material choice does not replace cycle, impact, temperature and wear testing.

## 12. Functional validation

Record at minimum:

- grip force by grasp type
- opening/closing time
- release time and failed-release events
- object-drop count
- false EMG activation rate
- re-don calibration time and repeatability
- targeted Box and Block Test (tBBT) or standard BBT when suitable
- fixed daily-object task battery
- comfort, skin inspection and suspension/rotation notes

## 13. Jarvis boundary

Jarvis may later perform deterministic engineering support such as mesh analysis, CAD parameter generation, revision comparison and test-data analysis.

**Jarvis must not command actuators, bypass the embedded safety controller, or become necessary for the worn V1 prosthesis to operate safely.**
