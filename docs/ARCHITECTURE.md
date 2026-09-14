# System Architecture

## Functional chain

```mermaid
flowchart LR
    U[User muscle intent] --> E[2-channel surface EMG]
    E --> A[Analog acquisition + filtering]
    A --> C[MCU control layer]
    C --> S[Grip state machine]
    S --> D1[Motor driver: index]
    S --> D2[Motor driver: 3-finger differential]
    S --> D3[Motor driver: thumb]
    D1 --> M1[Index tendon]
    D2 --> M2[Middle / ring / little differential]
    D3 --> M3[Thumb tendon / opposition]
    M1 --> H[Adaptive hand]
    M2 --> H
    M3 --> H
    H --> F[Object contact]
    F --> CS[Motor current + encoder feedback]
    CS --> C
```

## V1 design priorities

1. safe predictable behavior
2. comfortable length and fit
3. reliable useful grasps
4. low mass
5. low component count
6. local repairability
7. environmental hardening
8. advanced autonomy / ML later

## Actuation layout

### Actuator A - index

Independent index flexion improves pinch and tripod placement.

### Actuator B - middle/ring/little

One actuator drives an adaptive differential so the three fingers can conform around non-uniform objects.

### Actuator C - thumb

The thumb receives its own actuator because thumb position dominates practical grasp quality. The exact thumb mechanism is a major design decision and will be bench-tested before freezing the palm.

## Mechanical philosophy

- tendon-driven flexion
- passive spring/elastic extension
- mechanical compliance before software complexity
- modular fingers
- replaceable tendons
- metal pins/shafts where repeated bearing wear is expected
- service access from the dorsal side of the palm

## Control philosophy

The controller is layered so safety does not depend on EMG classification.

```mermaid
flowchart TD
    I[User intent] --> G[Grip command]
    G --> P[Position / velocity request]
    P --> L[Current and travel limits]
    L --> MD[Motor drive]
    MD --> FB[Encoder + current feedback]
    FB --> L
    W[Watchdog / fault monitor] --> L
    K[Hard disable] --> MD
```

## Packaging rule for this user case

Because the residual forearm is long, the wrist/adapter volume must be kept extremely short. Most actuation volume should live inside the prosthetic palm, not in a long distal extension after the residual limb.

## Modular boundaries

- socket / suspension module
- wrist / mechanical adapter
- hand module
- electronics module
- battery module
- EMG electrode module

A failure in one module should not require remaking the whole prosthesis.