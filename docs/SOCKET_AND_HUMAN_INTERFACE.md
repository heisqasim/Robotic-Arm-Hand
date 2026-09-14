# Socket and Human Interface

## Why this is a core subsystem

A hand can work perfectly on a bench and still fail as a prosthesis if the socket is painful, unstable, too long, difficult to don, or inconsistent for EMG electrodes.

The photographed case appears to have a long residual forearm ending close to the wrist level. That is favorable for preserving muscle sites, but it creates a strict **build-length problem**: the hand and connector must not make the prosthetic side excessively longer than the intact side.

The exact amputation level must be confirmed clinically.

## Inputs before a fitted socket

- medically stable residual limb
- 3D scan
- manual measurements for scale verification
- bony prominence map
- scar/sensitive-skin map
- circumference profile
- intact-arm/hand reference dimensions
- candidate EMG electrode sites
- range of motion and forearm rotation assessment

## Socket design goals

- secure suspension
- comfortable load transfer
- pressure relief over sensitive areas
- repeatable electrode contact
- low-profile distal adapter
- sweat management
- easy don/doff
- service access
- no sharp internal transitions

## Conceptual layers

```text
skin
  ↓
liner / interface as required
  ↓
load-distributing socket shell
  ↓
EMG access / electrode retention
  ↓
low-profile structural adapter
  ↓
prosthetic hand
```

## 3D scans are geometry, not medical clearance

A scan is useful for CAD and comparison, but it does not tell the team which areas can safely carry pressure. Clinical/prosthetics input is needed for final pressure-bearing and relief decisions.

## Fit iteration

Use disposable/low-cost printed test sockets or partial shells before committing to the final engineering material.

Evaluate:

- pressure marks
- skin response
- migration/slip
- rotation under load
- comfort during repeated grasping
- electrode signal after don/doff

## Privacy

Patient photographs, scans, identifying dimensions and medical notes must stay out of the public GitHub repository. Use an anonymous case identifier in engineering records.