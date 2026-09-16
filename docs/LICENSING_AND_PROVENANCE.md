# Licensing and Design Provenance

This project learns from open hardware, research prototypes and commercial products. “Open source” does not mean every design can be copied into this repository under any future license.

This document is engineering provenance guidance, not legal advice.

## Current repository license status

No license is selected here for Qasim's original project work. Until the repository owner deliberately chooses a license, do not assume that files from this repository or external projects can be freely relicensed.

Do not add a repository-wide license merely for convenience. The intended future use and the licenses of any incorporated external material must be reviewed first.

## External references

| Reference | Observed license | Project rule |
|---|---|---|
| OpenBionics/Prosthetic-Hands | CC BY-SA 4.0 | Safe to study. If CAD/material is adapted directly, attribution and ShareAlike obligations apply to the derivative material. Track exactly what was reused. |
| MelbourneUniHRL/X-Limb | CC BY-NC 4.0 | Reference/benchmark freely for research. Do **not** copy/adapt X-Limb CAD into our original design if we want to preserve future commercial/unrestricted use without permission. |
| pslade2/TactHand | Unlicense / public-domain dedication | Can be a comparatively permissive source, but still record provenance and verify any third-party files inside the repository before copying. |
| orthopus/01-myohand | CC0 1.0 | Comparatively permissive; still record source/revision for any direct reuse. |
| Research papers | publication-specific copyright/license | Use as engineering evidence. Do not copy figures, CAD supplements or code unless their specific license permits it. |
| Commercial products | proprietary | Benchmark published specifications and concepts only. Do not copy proprietary CAD, firmware, drawings or protected branding. |

## Provenance rule for every imported asset

Before committing copied or modified external CAD, code, drawings, PCB files, documentation or datasets, record:

- upstream project/name
- exact URL
- upstream revision/tag/commit if available
- original filename/path
- license
- whether the file is copied unchanged, modified, or only conceptually referenced
- required attribution text
- any ShareAlike / NonCommercial / redistribution restriction

Put this information beside the imported asset or in a dedicated `NOTICE`/manifest before merging it.

## Clean-room preference

For the core mechanical hand, prefer a **clean original CAD implementation** derived from measured requirements and general engineering concepts rather than editing an externally licensed CAD file.

Example:

- It is acceptable to learn the general principle of a whiffletree differential from published/open references and create an independently dimensioned mechanism for our hand.
- It is different to download a CC BY-SA part, modify its dimensions and then present the result as unrestricted original CAD. That derivative remains subject to the source license obligations.

When in doubt, keep a reference project as a benchmark and build the actual geometry from our own requirements.

## X-Limb warning

X-Limb is extremely useful technically but is licensed CC BY-NC 4.0. Because this project's long-term path is not yet fixed, **do not place modified X-Limb CAD/PCB source into the project's core original design tree** unless the owner explicitly accepts the NonCommercial restriction or obtains permission.

Use its publications, measurements, architecture and test results as research references instead.

## OpenBionics warning

The OpenBionics Prosthetic-Hands repository is CC BY-SA 4.0. Direct adaptations are allowed, including commercial use, but ShareAlike and attribution apply.

If we create an independently designed differential after studying the general mechanism, document the design process. If we directly modify their CAD, mark it clearly as a derivative and preserve the required license.

## Patient data is separate

Licensing is not the same as privacy. Patient photographs, scans, EMG data, medical notes and identifying measurements remain excluded from the public repository regardless of copyright permission.

## Sources checked

- OpenBionics Prosthetic-Hands license: https://github.com/OpenBionics/Prosthetic-Hands/blob/master/LICENSE.txt
- X-Limb license: https://github.com/MelbourneUniHRL/X-Limb/blob/master/LICENSE.md
- TactHand license: https://github.com/pslade2/TactHand/blob/master/LICENSE
- ORTHOPUS MyoHand license: https://github.com/orthopus/01-myohand/blob/master/LICENSE.md
