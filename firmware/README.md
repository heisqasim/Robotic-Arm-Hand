# Firmware Workspace

Firmware responsibilities:

- sample/process EMG
- run the grip state machine
- control three actuators
- enforce current/travel/time limits
- monitor watchdog and faults
- expose calibration/test telemetry

Safety limits belong below the high-level intent decoder. Future ML or Jarvis commands must never bypass motor-current, travel or fault limits.
