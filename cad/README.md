# CAD Workspace

Planned structure once CAD work begins:

- `concepts/` - early palm/finger/thumb concepts
- `finger_module/` - replaceable finger source CAD
- `differential/` - adaptive three-finger mechanism
- `thumb/` - thumb mechanism experiments
- `palm/` - actuator packaging and service cover
- `adapter/` - low-profile wrist/hand adapter
- `manufacturing/` - STL/3MF/STEP exports

Rules:

- keep source CAD and manufacturing exports separate
- dimension critical parts in millimetres
- version geometry by revision, not filenames such as `final_final2`
- do not commit patient-derived socket geometry to this public repository
- record material and print orientation with each functional export
