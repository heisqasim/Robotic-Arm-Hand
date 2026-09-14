# Reference Projects and Benchmarks

The project deliberately combines lessons from several open and commercial systems instead of cloning one hand.

## Open-source / research references

### OpenBionics Prosthetic-Hands

Repository: https://github.com/OpenBionics/Prosthetic-Hands

Useful lessons:

- low actuator count
- whiffletree/adaptive differential
- parametric CAD
- anthropometric scaling
- low-cost fabrication philosophy

Historical project claims: under 300 g and under USD 200 for the referenced design.

### Melbourne X-Limb

Repository: https://github.com/MelbourneUniHRL/X-Limb

Useful lessons:

- compact printed palm
- embedded actuation
- practical multi-grasp focus
- compliant finger design
- complete CAD/PCB/control reference

### Tact Hand

Repository: https://github.com/pslade2/TactHand

Useful lessons:

- full myoelectric prosthesis perspective
- common components and 3D printing
- assembly/BOM mindset
- affordability focus

### ORTHOPUS MyoHand

Repository: https://github.com/orthopus/01-myohand

Useful lessons:

- thumb design
- open hardware documentation
- separation between experimental DIY documentation and certified clinical products

### LibEMG

Repository: https://github.com/LibEMG/libemg

Useful lessons:

- real-time EMG acquisition/processing architecture
- feature extraction
- prediction/classification
- evaluation tooling

Use later after the direct-control V1 is stable.

## Commercial benchmark systems

### TASKA HandGen2

Manufacturer: https://www.taskaprosthetics.com/products/taska-gen2

Useful benchmark themes:

- IP67 waterproofing
- low-profile wrist options
- impact-tolerant daily-use philosophy
- published mass/carry/grip specifications

### Open Bionics Hero PRO

Manufacturer: https://openbionics.com/en/hero-pro/

Useful benchmark themes:

- Nylon PA12 construction
- IPX7 water resistance
- lightweight integrated system
- 3D-printed commercial-product precedent

### PSYONIC Ability Hand

Manufacturer: https://www.psyonic.io/ability-hand

Useful benchmark themes:

- pressure sensing
- vibrotactile feedback
- compliant/impact-resistant fingers
- IP64 splash resistance

### COVVI Hand

Manufacturer: https://www.covvi.com/covvi-hand/product-overview/

Useful benchmark themes:

- published grip-force targets
- silicone glove and fingertip wear strategy
- IP44 protection
- structural/load benchmarks

## Standards / engineering references

- ISO 14971:2019 - risk management for medical devices
- ISO 22523:2006 - external limb prostheses and orthoses requirements and test methods
- ISO/FDIS 22523 - replacement edition under development in 2026
- ISO/AWI 26209 - test methods for externally powered prosthetic hands, under development

## Design conclusion

The V1 architecture should borrow:

- adaptive differential -> OpenBionics
- compact practical hand integration -> X-Limb
- full-system affordability -> Tact
- thumb lessons -> ORTHOPUS
- EMG research tooling -> LibEMG
- robustness/water/serviceability targets -> commercial systems

No reference design should be treated as clinically safe merely because its files are open source.