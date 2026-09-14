# 3D Scan and Jarvis Integration

## Immediate workflow

The prosthetic project does not wait for Jarvis. Use existing scan/CAD tools now, then integrate the same workflow into Jarvis later.

```mermaid
flowchart LR
    P[iPhone photo capture / LiDAR reference] --> R[Photogrammetry reconstruction]
    R --> C[Mesh cleanup + scale verification]
    C --> M[Manual measurements]
    M --> CAD[CAD socket / adapter / hand overlay]
    CAD --> PRINT[3D print]
    PRINT --> FIT[Bench and fit validation]
    FIT --> REV[Revision]
    REV --> CAD
```

## Capture rules

For photogrammetry:

- residual limb stays completely still
- camera moves around it
- high overlap between images
- multiple height rings
- diffuse, consistent lighting
- known dimension / scale reference
- keep original photos

Do not combine image sets where the limb moved into one reconstruction job.

## Engineering data products

Store privately:

- raw images
- master high-resolution mesh
- cleaned/scaled mesh
- intact-side reference scan
- anonymous measurement sheet
- fit notes

Store in public GitHub only:

- generic scripts
- anonymous sample geometry, if explicitly safe to publish
- CAD templates with no patient-derived identifying geometry

## Jarvis future workspace

Jarvis can later provide a 3D engineering workspace without running heavy photogrammetry on the Oracle VM.

Recommended architecture:

```text
Jarvis Flutter UI
      |
      v
3D viewer (GLB preview)
      |
      v
Owner API / governed capability
      |
      v
Geometry worker
  - Trimesh
  - Open3D
  - CadQuery / OpenCascade
      |
      v
Private geometry storage
```

### Division of work

The iPhone or dedicated photogrammetry engine performs image reconstruction.

The Jarvis server performs lighter deterministic tasks such as:

- mesh validation
- alignment
- cross-sections
- dimensions
- volume
- comparison between scans
- CAD parameter generation
- revision tracking

The browser/device GPU renders the interactive 3D view.

## Digital twin direction

A future anonymous case workspace can link:

- residual-limb scan
- intact-hand reference
- socket revision
- prosthetic hand revision
- EMG electrode map
- test results
- fit observations

This is an engineering aid, not a clinical decision system.