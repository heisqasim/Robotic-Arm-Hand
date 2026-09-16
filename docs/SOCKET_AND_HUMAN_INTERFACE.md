# Socket and Human Interface

## Why this is a core subsystem

A hand can work perfectly on a bench and still fail as a prosthesis if the socket is painful, unstable, too long, hot, sweaty, difficult to don, or inconsistent for the intent sensors.

The photographed case appears to have a long residual forearm ending close to wrist level. That is favorable for preserving muscle sites and possibly physiological forearm rotation, but it creates a strict **build-length problem**.

The exact amputation level and functional range of motion must be confirmed clinically.

## Case-specific design requirements

- Preserve the user's own pronation/supination when it is adequate.
- Avoid powered wrist rotation in V1 unless functional testing shows a real need.
- Distal wrist/adapter build-height target: **<=25 mm**.
- Stretch target: <=15 mm if anatomy and mechanical packaging allow it.
- Check total prosthetic length against the intact side before freezing the hand/socket interface.
- Keep heavy components as proximal as practical to reduce distal moment.

The 25 mm target is informed by current transcarpal commercial hardware, not treated as a universal clinical limit.

## Inputs before a fitted socket

- medically stable residual limb
- 3D scan
- manual measurements for scale verification
- intact-side reference dimensions
- bony prominence map
- scar/sensitive-skin map
- circumference profile
- candidate EMG and possible FMG sensing sites
- range of motion and pronation/supination assessment
- sweat/heat history during daily activity
- actual user task priorities

## Socket design goals

- secure suspension
- anti-rotation under grasp/carry loads
- comfortable load transfer
- pressure relief over sensitive areas
- repeatable sensor contact
- low-profile distal adapter
- ventilation / moisture paths
- easy don/doff
- service access
- wire/sensor strain relief
- no sharp internal transitions
- cleanable skin-facing surfaces

## Sweat is an interface problem, not a late environmental feature

In hot conditions, sweat can simultaneously degrade comfort, suspension and electrode stability.

Design the first fitted prototypes around:

- ventilation openings where structurally safe
- lateral airflow rather than sealed dead volume where possible
- drainage/drying paths
- corrosion-resistant nearby hardware
- electrode retention that does not depend only on adhesive
- separation between skin-facing wet zones and protected electronics
- removable/cleanable interface parts when practical

Commercial ventilated 3D-printed sockets such as Open Bionics Hero FLEX are useful proof that ventilation and adjustable electrode placement can be treated as primary product features.

## Sensor integration

### sEMG baseline

The V1 socket must make the same electrode pair land in approximately the same anatomical location and pressure after each don/doff.

Evaluate:

- electrode orientation
- contact pressure
- cable strain
- sweat accumulation
- signal after repeated don/doff
- whether a dry/reusable contact strategy becomes preferable to disposable adhesive electrodes for the wearable version

### FMG fallback experiment

If EMG remains unstable after good placement and socket work, reserve the possibility of testing a small pressure/force sensor array around the forearm. This is a research fallback, not a reason to complicate the first socket.

## Conceptual layers

```text
skin
  ↓
cleanable liner / interface as required
  ↓
load-distributing and ventilated socket shell
  ↓
repeatable sensor/electrode retention
  ↓
short structural adapter (target <=25 mm)
  ↓
prosthetic hand
```

## 3D scans are geometry, not medical clearance

A scan is useful for CAD and comparison, but it does not tell the engineering team which areas can safely carry pressure. Clinical/prosthetics input is needed for final pressure-bearing and relief decisions.

Do not infer tissue tolerance from a photo or mesh.

## Fit iteration

Use inexpensive printed test sockets or partial shells before committing to the final engineering material.

Evaluate after defined supervised wear intervals:

- pressure marks
- skin response
- pain/discomfort
- heat/sweat accumulation
- migration/slip
- rotation under load
- ease of don/doff
- signal quality after don/doff
- signal quality after warming/sweat
- distal adapter alignment and total length

The socket is not accepted merely because it “fits” at rest.

## Body-contact materials

Skin-contact choices belong inside the project risk process. Track ISO 10993-1:2025 when evaluating biological safety of materials/components that directly or indirectly contact the body.

This does not mean every student prototype is formally tested to the standard; it means material choice and exposure duration must not be treated casually.

## Privacy

Patient photographs, scans, identifying dimensions, medical notes and raw EMG recordings must stay out of the public GitHub repository. Use an anonymous case identifier in engineering records.