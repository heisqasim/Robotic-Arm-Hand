# Red-Team Review — 2026-09

This document records a deliberate attempt to break the project strategy before more hardware is built. The review compares the current plan with recent commercial systems, open research, user-needs evidence, control research, and standards activity available in 2025–2026.

## Executive conclusion

The project direction is fundamentally sound, but several assumptions were too rigid.

What survives the review:

- user-centered, low-cost and repairable design goal
- low-profile fitting for a very long residual forearm / wrist-level case
- underactuated tendon mechanics rather than maximum actuator count
- direct surface-EMG control as the first wearable control mode
- deterministic safety below the intent-decoding layer
- modular fingers, replaceable tendons and staged bench validation
- no dependency on machine learning for V1 usability

What changes after the review:

1. **Three actuators are now a baseline, not a frozen truth.** A two-actuator architecture must be bench-compared against it before the palm is frozen.
2. **Build height becomes a quantified design problem.** For this user case, the distal adapter target is <=25 mm; <=15 mm is a stretch target if anatomy and mechanics allow it.
3. **Preserved biological pronation/supination should be used instead of adding a powered wrist in V1**, if clinical examination confirms adequate forearm rotation.
4. **Sweat, ventilation and repeatable electrode contact move into the socket design stage.** They are not late environmental extras.
5. **sEMG remains the primary V1 interface, but the controller must not be architecturally locked to EMG.** Force myography (FMG) is the low-cost fallback research path; HD-EMG and sonomyography remain later research options.
6. **Direct control should command velocity/rate rather than absolute finger position.** Re-calibration after don/doff and robustness tests across posture, sweat and fatigue are mandatory.
7. **Mechanical overload protection must be intentional.** Replaceable fingers are not enough; investigate compliant/breakaway joints and series elasticity.
8. **Holding an object must not require near-stall motor current.** Evaluate self-locking transmissions, brakes or latches, while also providing a manual emergency release.
9. **Sealing features are designed into CAD early even though water-resistance claims are validated later.**
10. **The validation plan becomes quantitative** rather than only descriptive.
11. **External design provenance and licensing must be tracked** before copying any CAD or firmware.
12. **Jarvis is an engineering-analysis tool only. It must not be in the live safety/control loop of a worn V1 prosthesis.**

## Why the three-actuator assumption was challenged

The current baseline gives independent index control, a grouped middle/ring/little differential, and a thumb actuator. That is a reasonable way to preserve pinch/tripod function while keeping actuator count low.

However, current evidence shows that useful grasping does not scale directly with actuator count:

- Pisa/IIT SoftHand Pro uses a strongly underactuated synergy and was reduced to about 290 g with quick-disconnect wrist and 177.8 mm hand length while retaining adaptive grasping.
- A 2024 IROS prosthetic-hand study demonstrated a two-motor underactuated series-elastic architecture with position, force/impedance, slip-related and safe-interaction behaviors, while also identifying friction and holding-power issues.
- At the other extreme, a 2025 Nature Communications hand achieved 19 DOF at 370 g using 38 SMA actuators, proving high dexterity is possible but with thermal/control/manufacturing complexity that is inappropriate for our first repairable daily-use candidate.

Therefore the correct engineering question is not “Can we fit three motors?” but “Does the independent-index motor provide enough functional benefit to justify its mass, volume, wiring and energy?”

### Architecture gate

Before palm freeze, build or simulate two variants using the same finger geometry:

- **Variant A — 3 actuators:** index independent; middle/ring/little differential; thumb independent.
- **Variant B — 2 actuators:** four-finger adaptive synergy/differential; thumb independent or manually pre-positioned depending the experiment.

Compare pinch repeatability, tripod placement, power grasp, opening width, mass, build volume, current, failure modes and service complexity. Keep the third actuator only if measured utility justifies it.

## The biggest case-specific risk: build length

This user appears to have an extremely long residual forearm / wrist-level limb. Current commercial systems confirm that this is a distinct engineering problem, not a cosmetic detail.

Ottobock's wrist.transcarpal is specifically designed for long residual limbs up to transcarpal level and publishes a 25 mm build height and 50 g mass. It also explicitly relies on preserved physiological pronation/supination. Ottobock's new 2026 speedhand emphasizes reduced device length and modular transcarpal/short wrists. TASKA also offers low-profile configurations.

Our V1 should therefore:

- preserve biological forearm rotation when available
- avoid powered wrist rotation in V1 unless a clinical/function test proves it necessary
- make distal adapter build height a first-class CAD parameter
- measure the intact-side anatomical length before finalizing the palm/wrist stack

## User needs over technical spectacle

The 2026 systematic review of upper-limb prosthesis users reinforces a consistent message: comfort, weight, useful function, intuitive control and reliability strongly affect acceptance. More technology does not automatically improve real-world adoption.

Therefore V1 prioritizes, in order:

1. fit and comfort
2. low distal mass and correct length
3. predictable release and grasp
4. useful power/pinch/tripod/hook tasks
5. repairability and robustness
6. environmental tolerance
7. additional dexterity or autonomy only after the above are proven

## Control-interface red team

Two-channel sEMG remains the best first interface because it is affordable, well-understood and locally serviceable. But recent reviews continue to show instability from electrode shift, changing skin contact, fatigue, posture and noise. HD-EMG offers richer information but currently adds electrode, cabling, processing and fitting complexity. A 2026 review also highlights clinically tested biomechanical alternatives including sonomyography, force myography and mechanomyography.

The updated architecture therefore uses a **sensor abstraction**:

```text
human intent sensor
    |-- 2-channel sEMG          <- V1 baseline
    |-- low-cost FMG array      <- fallback experiment
    |-- HD-EMG                  <- later research
    |-- sonomyography / MMG     <- later research
            |
            v
normalized intent interface
            |
            v
safety-limited grasp controller
```

The hand should remain usable when the sensing front end changes.

## Velocity control

A 2026 study with able-bodied and limb-difference participants compared co-adaptive position and velocity myocontrol for a 3-DOF prosthesis. Velocity control produced lower errors, higher success/path efficiency and lower workload overall, although position control enabled more simultaneous actuation.

For our direct-control V1, muscle amplitude should therefore primarily command **closing/opening velocity (or rate)**, while current and travel limits determine safe force and endpoint behavior.

## Mechanical robustness: what the newest products teach

Recent commercial development is moving toward durability features rather than only extra grip modes:

- Open Bionics Hero RGD uses Nylon PA12, titanium parts, brushless motors, a shock-absorbing TPU palm and spring-loaded fingers.
- PSYONIC and TASKA also emphasize impact tolerance/compliance.
- Ottobock speedhand combines compact length, fast motion and strong grip rather than pursuing individually articulated fingers.

For us this means:

- a finger should survive ordinary knocks without transmitting the full shock into gearbox teeth
- add a replaceable or resettable overload/breakaway concept at vulnerable joints
- investigate series elasticity in the tendon path
- protect pulleys/tendons from abrasion and side loading
- use plain tough PA12 as a strong default for impact-critical printed structure; reserve filled nylons for parts where stiffness is more valuable than toughness

## Holding power and emergency release

A hidden failure mode in many student hands is holding an object by continuously driving a motor near stall. That wastes battery and heats motors/drivers.

V1 must measure hold power. If necessary, test:

- self-locking gear reduction
- normally passive brake
- tendon latch / mechanical hold

But any self-locking or latched design creates a new hazard: a dead battery or controller fault must not leave the user trapped onto an object. A **manual mechanical emergency release** is therefore a V1 requirement.

## Socket and heat/sweat

For Baghdad/Iraq conditions, sweat is not a late waterproofing issue. It directly affects:

- comfort
- skin condition
- suspension
- EMG contact impedance and electrode movement
- corrosion

Open Bionics Hero FLEX is a useful current benchmark because its socket is 3D-scanned/printed, ventilated, and uses adjustable wireless EMG electrodes. We do not need to clone it, but the design lesson is immediate: airflow, drainage/dry zones, electrode retention and don/doff repeatability belong in the first fitted socket experiments.

## Quantitative V1 development targets

These are engineering targets, not clinical claims or certification limits. Revise them when measured user geometry and test evidence justify it.

| Metric | Development target |
|---|---|
| Distal adapter build height | <=25 mm; stretch <=15 mm |
| Hand module mass | <=350 g target; review architecture above 400 g |
| Full wearable system mass | <=600 g target if feasible for this case |
| Power grip | >=30 N baseline; >=50 N stretch |
| Pinch | >=10–15 N baseline; >=20 N stretch |
| Full open-to-close | <=1.0 s target |
| Bench mechanism gate | >=10,000 cycles before wearable trials |
| Extended supervised-use gate | >=100,000 full-hand cycles |
| Development durability target | 250,000 cycles |

Grip-force testing should align where practical with the grasp families now appearing in ISO/AWI 26209: cylindrical grasp, pinch and lateral pinch.

## Functional validation update

Bench metrics alone do not prove usefulness. Add a repeatable human-performance set:

- a fixed daily-object battery: bottle/cup, bag handle, spoon/fork, phone, door handle, pen/small object, clothing interaction
- release-time and failed-release count
- object-drop count
- targeted Box and Block Test (tBBT) or standard Box and Block Test when appropriate
- don/doff repeatability and calibration time
- comfort, skin inspection and pressure/suspension observations
- false activation rate and re-don control repeatability

The 2025 tBBT study in transradial prosthesis users found good-to-excellent test-retest reliability and excellent interrater reliability, making it useful for our supervised evaluation.

## Standards update

Track at minimum:

- ISO 14971:2019 — risk management; still current after 2025 review
- ISO 10993-1:2025 — biological safety evaluation for body-contacting medical-device materials
- ISO 22523:2006 — current published external prosthesis/orthosis requirements standard
- ISO/FDIS 22523 Edition 2 — currently in final approval and expected to replace the 2006 edition
- ISO/AWI 26209 — new 2026 work item for grasp-force and repetitive-durability tests of externally powered prosthetic hands

These standards guide engineering discipline; they do not certify this student/research device.

## What we deliberately do not chase in V1

- 19-DOF or biological-hand-equivalent dexterity
- 16+ channel HD-EMG
- ultrasound/sonomyography hardware
- computer vision or shared autonomy
- tactile-feedback research as a dependency
- powered wrist rotation when the user's own forearm rotation is usable
- claimed IP ratings before defined water-ingress testing

These remain valid V1.1/V2 research directions after the basic prosthesis is genuinely useful.

## Sources reviewed

- 2026 systematic review of upper-limb prosthesis user needs: https://doi.org/10.3390/s26020734
- SoftHand Pro platform: https://pmc.ncbi.nlm.nih.gov/articles/PMC9906824/
- 2024 IROS series-elastic prosthetic hand: https://doi.org/10.1109/IROS58592.2024.10803048
- 2025 19-DOF lightweight prosthetic hand: https://doi.org/10.1038/s41467-025-56352-5
- 2026 co-adaptive velocity/position myocontrol: https://doi.org/10.1109/TNSRE.2026.3657400
- 2025 HD-EMG review: https://doi.org/10.3389/fnins.2025.1655257
- 2026 muscle-deformation sensing review: https://doi.org/10.1109/TNSRE.2026.3710283
- Ottobock wrist.transcarpal: https://shop.ottobock.us/Prosthetics/Upper-Limb-Prosthetics/Myo-Hands-and-Components/wrist-transcarpal/p/10V64~51
- Ottobock speedhand: https://www.ottobock.com/en-us/b2b-product/8E2
- Open Bionics Hero RGD: https://openbionics.com/hero-rgd/
- Open Bionics Hero FLEX: https://openbionics.com/en/heroflex/
- 2025 targeted Box and Block Test validation: https://doi.org/10.1016/j.arrct.2025.100427
- ISO 14971: https://www.iso.org/standard/72704.html
- ISO 10993-1:2025: https://www.iso.org/standard/10993-1
- ISO/FDIS 22523: https://www.iso.org/standard/80242.html
- ISO/AWI 26209: https://www.iso.org/standard/92838.html
