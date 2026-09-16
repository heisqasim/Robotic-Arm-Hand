# Reference Projects and Benchmarks

The project deliberately combines lessons from several open/research and commercial systems instead of cloning one hand. References are used for engineering evidence and comparison; direct file reuse must follow `LICENSING_AND_PROVENANCE.md`.

## Open-source / research references

### OpenBionics Prosthetic-Hands

Repository: https://github.com/OpenBionics/Prosthetic-Hands

Useful lessons:

- low actuator count
- whiffletree/adaptive differential
- parametric CAD
- anthropometric scaling
- low-cost fabrication philosophy

License note: CC BY-SA 4.0. Direct derivatives carry attribution/share-alike obligations.

### SoftHand Pro

Paper/platform: https://pmc.ncbi.nlm.nih.gov/articles/PMC9906824/

Useful lessons:

- strong underactuation/synergy instead of one motor per finger
- adaptive grasp through compliance
- user-centered reduction of size and mass
- published updated platform around 290 g including quick-disconnect wrist and 177.8 mm hand length

This is one of the strongest reasons to bench-test a two-actuator architecture instead of assuming three actuators are automatically necessary.

### Melbourne X-Limb

Repository: https://github.com/MelbourneUniHRL/X-Limb

Useful lessons:

- compact printed palm
- embedded actuation
- practical multi-grasp focus
- compliant finger design
- complete CAD/PCB/control reference

License warning: CC BY-NC 4.0. Use as a technical reference unless the project explicitly accepts its NonCommercial restriction or obtains permission.

### Tact Hand

Repository: https://github.com/pslade2/TactHand

Useful lessons:

- full myoelectric prosthesis perspective
- common components and 3D printing
- assembly/BOM mindset
- affordability focus

License: Unlicense/public-domain dedication in the repository; still track provenance for reused files.

### ORTHOPUS MyoHand

Repository: https://github.com/orthopus/01-myohand

Useful lessons:

- thumb design
- open hardware documentation
- separation between experimental DIY documentation and certified clinical products

License: CC0 1.0 in the repository.

### UJI-Hand MK4 — 2026

Dataset/CAD: https://zenodo.org/records/21489522

Useful lessons:

- recent student-team open prosthetic development
- body-powered underactuation
- five-finger cable routing / elastic return
- CAD/STEP/STL documentation and additive fabrication
- reminder that mechanical simplicity can deliver useful function without adding electronics

It is body-powered, so it is a mechanical reference rather than our V1 control architecture.

### Series-elastic two-motor prosthetic hand — IROS 2024

Paper: https://doi.org/10.1109/IROS58592.2024.10803048

Useful lessons:

- two-motor underactuated architecture
- series elasticity for morphological grasp, force/impedance behavior and safer contact
- cable friction and sensor resolution are real limitations
- efficient holding may require a brake/locking strategy

This motivates a **series-elastic bench experiment**, not automatic adoption.

### Lightweight 19-DOF SMA hand — Nature Communications 2025

Paper: https://doi.org/10.1038/s41467-025-56352-5

Published results include:

- 19 DOF
- 38 SMA actuators
- hand part about 0.22 kg
- full prosthesis about 0.37 kg
- 33 standard + 6 complex grasp modes

Useful lesson: very high dexterity can coexist with low mass, but the SMA thermal/control/manufacturing complexity does not match our first locally repairable V1. Treat it as a state-of-the-art research benchmark, not a target architecture.

### LibEMG

Repository: https://github.com/LibEMG/libemg

Useful lessons:

- real-time EMG acquisition/processing architecture
- feature extraction
- prediction/classification
- evaluation tooling

Use later after direct-control V1 is stable.

### Hannes / IIT control research

Recent control reference: https://doi.org/10.1109/TNSRE.2026.3657400

Useful lessons:

- real prosthesis platform and user studies
- co-adaptive myocontrol research
- 2026 velocity-vs-position study supports velocity-based proportional control as a strong starting point
- shared autonomy / vision-assisted grasping exists but belongs after core manual usability

### HD-EMG and alternative muscle sensing

HD-EMG review (2025): https://doi.org/10.3389/fnins.2025.1655257

Muscle-deformation sensing review (2026): https://doi.org/10.1109/TNSRE.2026.3710283

Useful lessons:

- HD-EMG can provide richer spatial intent information but still faces electrode-shift, fitting, cabling, power and embedded-compute challenges
- clinically tested noninvasive alternatives include force myography, sonomyography, mechanomyography and myokinetic interfaces
- V1 should keep 2-channel sEMG, while firmware remains sensor-agnostic and FMG becomes the first fallback experiment if needed

## Commercial benchmark systems

Commercial products are specification/architecture benchmarks only; they are not source designs.

### Ottobock speedhand — launched 2026

Product: https://www.ottobock.com/en-us/b2b-product/8E2

Published benchmark points:

- Ottobock's shortest current myoelectric hand
- 368–425 g depending size
- 103–109 mm length to base plate depending size
- up to 300 mm/s proportional speed
- up to 24 lbf (~107 N) proportional grip force
- optional AutoGrasp thumb sensor
- modular wrist family including transcarpal/short options

Useful lessons:

- compact build length is a first-class product feature
- strong useful tripod-style function can be prioritized over many independently articulated fingers
- slip/autograsp sensing can be added without making tactile sensing a V1 dependency

### Ottobock wrist.transcarpal — current low-build-height benchmark

Product: https://shop.ottobock.us/Prosthetics/Upper-Limb-Prosthetics/Myo-Hands-and-Components/wrist-transcarpal/p/10V64~51

Published benchmark points:

- designed specifically for long residual limbs up to transcarpal level
- 25 mm build height
- 50 g
- requires physiological pronation/supination for full function

This directly informs our <=25 mm distal-adapter target and reinforces preserving biological forearm rotation instead of adding a powered wrist in V1.

### TASKA HandGen2

Manufacturer: https://www.taskaprosthetics.com/products/taska-gen2

Useful benchmark themes:

- IP67 waterproofing
- low-profile wrist option
- impact-tolerant daily-use philosophy
- published mass/carry/grip specifications
- from 556 g system/hand configuration benchmark on manufacturer page

### Open Bionics Hero PRO

Manufacturer: https://openbionics.com/en/hero-pro/

Useful benchmark themes:

- Nylon PA12 construction
- IPX7 water resistance
- lightweight integrated-system emphasis
- 3D-printed commercial-product precedent

### Open Bionics Hero RGD — current rugged benchmark

Manufacturer: https://openbionics.com/hero-rgd/

Useful benchmark themes:

- Nylon PA12 + titanium
- brushless motors
- shock-absorbing TPU palm
- spring-loaded fingers for impact tolerance
- 35 kg published carrying-capacity benchmark
- waterproof/rugged use positioning

Design lesson: impact protection, compliant interfaces and ordinary durability matter as much as extra grip modes.

### Open Bionics Hero FLEX

Manufacturer: https://openbionics.com/en/heroflex/

Useful benchmark themes:

- patient 3D scanning and printed custom socket
- ventilation / lateral airflow
- sweat-management emphasis
- adjustable wireless MyoPod EMG electrodes
- modular terminal-device concept

Design lesson: sweat, ventilation and repeatable sensing belong inside the socket architecture from the beginning.

### PSYONIC Ability Hand

Manufacturer: https://www.psyonic.io/ability-hand

Useful benchmark themes:

- pressure sensing
- vibrotactile feedback
- compliant/impact-resistant fingers
- water/splash resistance

### COVVI Hand

Manufacturer: https://www.covvi.com/covvi-hand/product-overview/

Useful benchmark themes:

- six-actuator multi-articulation benchmark
- published ~90 N power-grip benchmark
- fingertip sensing
- silicone glove/fingertip wear strategy
- IP44 protection

Useful contrast: dexterity and sensing can rise quickly with actuator count, but so do mass, packaging and complexity.

## User-needs evidence

2026 systematic review: https://doi.org/10.3390/s26020734

Major design-relevant themes across user reports:

- comfort
- low weight
- useful functionality
- intuitive control
- reliability
- fit/personalization

This is why V1 does not chase maximum DOF as its top metric.

## Functional assessment references

2025 targeted Box and Block Test validation in upper-extremity prosthesis users:
https://doi.org/10.1016/j.arrct.2025.100427

Useful lesson: measure repeatable grasp/transport/release performance, not just maximum grip force or successful demonstrations.

## Standards / engineering references

- ISO 14971:2019 — risk management for medical devices; confirmed current in 2025
- ISO 10993-1:2025 — biological safety evaluation for body-contacting medical-device materials
- ISO 22523:2006 — current published external limb prostheses/orthoses requirements and test methods
- ISO/FDIS 22523 Edition 2 — final approval stage in 2026, intended to replace the 2006 edition
- ISO/AWI 26209 — 2026 work item for force and repetitive durability testing of externally powered prosthetic hands

## Current design conclusion

The V1 should borrow **principles**, not copy one product:

- adaptive differential / low actuator count -> OpenBionics + SoftHand evidence
- compact practical integration -> X-Limb and current commercial low-build-height systems
- full-system affordability / repairability -> Tact + our local-manufacturing constraints
- thumb and cable-routing lessons -> ORTHOPUS / UJI-Hand / research references
- direct velocity myocontrol -> 2026 Hannes control evidence
- sensing architecture flexibility -> sEMG now, FMG comparison if needed, HD-EMG/SMG later
- impact/water/serviceability thinking -> Hero RGD, TASKA, PSYONIC
- socket ventilation and repeatable electrode placement -> Hero FLEX and current HD-EMG interface research

No reference design should be treated as clinically safe merely because its files are open source.