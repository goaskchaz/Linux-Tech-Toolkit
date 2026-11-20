# Linux-Tech-Toolkit — Software Requirements Specification (SRS)

**Version:** 1.0.0 (baseline draft)  
**Date:** 2026-11-19  
**Status:** Proposed — requirements defined; implementation and hardware validation pending  
**Repository:** https://github.com/goaskchaz/Linux-Tech-Toolkit

## 1. Purpose
Define a portable, reproducible, free-software-first Linux engineering workstation for computer maintenance, disk recovery, MCU/MPU programming, PLC experimentation, network analysis, electronics design and simulation, amateur radio programming, and AF/RF test and measurement. An older HP Pavilion laptop is the first target, but the toolkit must not be HP-specific.

## 2. Governing principles
- Define the full capability scope now; implement only approved, prioritized work.
- Keep requirements, application selection, provisioning and validation distinct.
- Prefer free/open-source tools; document any proprietary hardware drivers, firmware, vendor software or licensing exceptions.
- Use Linux-native tools on Linux. PMC is the proposed provisioning orchestrator, not a currently verified Linux installer.
- Prioritize read-only diagnosis, reversibility, electrical safety, reproducibility and offline use.
- Record objective verification evidence before marking a feature complete.

## 3. Related specifications
- [Architecture](Architecture.md): component boundaries, PMC interface and provisioning workflow.
- [Roadmap](Roadmap.md): priorities, dependencies and phase acceptance gates.
- [Installation](Installation.md): preliminary installation procedure.
- [Hardware](Hardware.md): target inventory and interfaces.
- [Software Catalog](Software-Catalog.md): initial candidate applications and official sources.

## 4. Roles and operational modes
**Roles:** workstation owner/administrator, technician/operator, maintainer/developer. Initial deployment may use one person in all roles; privileged operations still require deliberate authorization.

**Modes:** inspect (read-only), plan/dry-run, apply approved installation, verify, repair/resume, export sanitized report. Hazardous device operations are separate, explicitly confirmed procedures.

## 5. Requirements convention
Each requirement has a stable identifier. **P0** = critical prerequisite; **P1** = high; **P2** = medium; **P3** = later. Priorities are initial suggestions and can change independently of the requirement ID. Acceptance checks are listed in Section 16.

## 6. Platform and hardware requirements
- **SYS-001 [P0]** Support both a lightweight graphical desktop and full terminal access.
- **SYS-002 [P0]** Select Linux distribution only after live-USB compatibility testing of the actual laptop.
- **SYS-003 [P0]** Identify CPU/architecture, RAM, disks, BIOS/UEFI, USB, Wi-Fi/Ethernet, graphics and connected adapters.
- **SYS-004 [P0]** Remove dependency on HP OEM software while preserving required firmware functionality.
- **SYS-005 [P0]** Document minimum and recommended hardware resources for each application profile.
- **SYS-006 [P1]** Support common tasks offline after installation; identify tasks requiring network access.
- **SYS-007 [P1]** Support SSH, local serial consoles and multiple USB peripherals where compatible.
- **SYS-008 [P1]** Separate configuration, data, logs, images and temporary files.

## 7. Application management
- **APP-001 [P0]** Maintain an approved application catalog with name, purpose, category, license, source, version policy, OS/architecture compatibility, dependencies and test method.
- **APP-002 [P0]** Distinguish proposed, approved, installed, configured, tested, failed and deprecated applications.
- **APP-003 [P0]** Support selectable profiles: Core, Computer, MCU, PLC, Network, Electronics and Radio/RF.
- **APP-004 [P1]** Install and update from trusted distribution package repositories first; support verified alternatives as required.
- **APP-005 [P1]** Detect already-installed packages and avoid redundant installation.
- **APP-006 [P1]** Record installed versions, package sources, configuration changes and results.
- **APP-007 [P1]** Support removal, repair and configuration backup where feasible.
- **APP-008 [P2]** Support prepared offline packages and dependency bundles where licensing permits.
- **APP-009 [P1]** Provide documented launch commands and optional desktop shortcuts.
- **APP-010 [P1]** Maintain tested hardware/application compatibility and flag unsupported versions.

## 8. Computer maintenance and OS recovery
- **COMP-001 [P1]** Identify physical drives, partitions, filesystems, capacities and health indicators.
- **COMP-002 [P1]** Provide SMART/NVMe health diagnostics and readable reports.
- **COMP-003 [P1]** Create, verify and restore disk images on noncritical test media.
- **COMP-004 [P1]** Partition, format and mount removable disks with explicit target selection.
- **COMP-005 [P1]** Prepare Linux and Windows installation/recovery media; Windows licensing remains separate.
- **COMP-006 [P1]** Support HDD overwrite and SSD-specific sanitize methods only after media-appropriate safety checks.
- **COMP-007 [P1]** Prevent automatic modification of the boot/system disk and require confirmation for destructive operations.
- **COMP-008 [P2]** Support filesystem troubleshooting, data recovery and backup verification.

## 9. MCU, MPU and embedded development
- **EMB-001 [P1]** Provide C/C++, Python, Git, compilers, debuggers and an open-source editor.
- **EMB-002 [P1]** Support supported Arduino, Teensy and Raspberry Pi development workflows.
- **EMB-003 [P1]** Detect USB serial devices and communicate via UART/RS232/RS485 using appropriate adapters.
- **EMB-004 [P1]** Support firmware build, upload, readback/verification where available, and version tracking.
- **EMB-005 [P1]** Support SWD/JTAG debugging for compatible target devices and probes.
- **EMB-006 [P2]** Save serial logs, build output and debug traces.
- **EMB-007 [P1]** Document voltage levels, pinouts, target power and device-specific firmware risks.

## 10. PLC and industrial communication
- **PLC-001 [P1]** Provide free PLC programming/simulation tools for laboratory use.
- **PLC-002 [P1]** Support Modbus TCP and Modbus RTU clients, servers and diagnostics.
- **PLC-003 [P1]** Document supported industrial adapters and electrical isolation requirements.
- **PLC-004 [P1]** Prevent unintended writes to PLC registers, coils or physical outputs.
- **PLC-005 [P2]** Capture and log permitted protocol traffic and test outcomes.
- **PLC-006 [P1]** Clearly distinguish laboratory PLC tools from safety-rated production controllers.
- **PLC-007 [P3]** Evaluate additional PLC protocols and vendor environments case by case.

## 11. Network diagnostics
- **NET-001 [P1]** Capture and inspect network packets on authorized interfaces.
- **NET-002 [P1]** Provide authorized discovery, port diagnostics, latency, route and throughput tests.
- **NET-003 [P1]** Support SSH and remote management of test devices.
- **NET-004 [P1]** Record target scope, interface, time, commands and test results.
- **NET-005 [P1]** Configure firewall, permissions and capture privileges safely.
- **NET-006 [P2]** Support separate test and management network interfaces where hardware permits.

## 12. Electronics design, simulation and measurement
- **ELEC-001 [P2]** Create/edit electronic schematics and reusable component libraries.
- **ELEC-002 [P2]** Design PCB layouts and export fabrication files.
- **ELEC-003 [P2]** Simulate analog circuits using SPICE, including transient and frequency analysis.
- **ELEC-004 [P2]** Simulate digital logic circuits.
- **ELEC-005 [P2]** Support basic MCU/circuit simulation where supported by chosen applications.
- **ELEC-006 [P2]** Capture and decode UART, SPI, I2C and other supported digital signals with compatible logic analyzers.
- **ELEC-007 [P2]** Save simulation projects, waveforms and measurement results.
- **ELEC-008 [P2]** Support 3D PCB inspection and enclosure/mechanical design.
- **ELEC-009 [P2]** Evaluate KiCad, Qucs-S, ngspice, SimulIDE, Logisim Evolution, PulseView/sigrok and FreeCAD.
- **ELEC-010 [P2]** Document measurement limits, sample rates and device voltage ratings.

## 13. Radio programming, AF and RF testing
- **RAD-001 [P2]** Program compatible amateur radios using CHIRP and appropriate cables.
- **RAD-002 [P2]** Back up and document radio configurations before writing changes.
- **RAD-003 [P2]** Generate selectable AF tones and sweeps using supported audio hardware.
- **RAD-004 [P2]** Record/analyze AF waveforms and frequency; report measurement uncertainty where known.
- **RAD-005 [P2]** Receive and display RF signals using compatible SDR receivers.
- **RAD-006 [P2]** Support antenna SWR, impedance and filter testing with compatible VNAs.
- **RAD-007 [P3]** Measure RF carrier frequency and output power using appropriately protected, rated and calibrated instruments.
- **RAD-008 [P3]** Generate controlled RF test signals with suitable signal-generation hardware.
- **RAD-009 [P3]** Support receiver sensitivity, selectivity and modulation tests with suitable calibrated instruments.
- **RAD-010 [P3]** Record test frequency, modulation, level, instrument identity, calibration and results.
- **RAD-011 [P0]** Never connect transmitter power directly to unprotected SDR, VNA or laptop inputs.
- **RAD-012 [P0]** Require RF load/attenuation/input-rating checks and compliance with applicable operating rules.

## 14. PMC integration and automation
- **PMC-001 [P0]** Define a versioned machine-readable manifest contract between LTT and PMC.
- **PMC-002 [P0]** Detect OS, architecture, available storage, network and relevant hardware before planning.
- **PMC-003 [P0]** Resolve application dependencies, profiles, priorities and incompatible versions.
- **PMC-004 [P0]** Show a dry-run plan with exact proposed changes and required privileges.
- **PMC-005 [P1]** Download from approved sources, verify authenticity where supported, install and configure approved packages.
- **PMC-006 [P1]** Verify installed state and execute non-destructive acceptance tests.
- **PMC-007 [P1]** Log every step with timestamps, outcomes and recovery instructions.
- **PMC-008 [P1]** Support idempotent reruns, interrupted-install resume and controlled retry.
- **PMC-009 [P1]** Support incremental changes as requirements, priorities and manifests evolve.
- **PMC-010 [P0]** Never execute disk erasure, firmware flashing, PLC output changes or RF transmission as automatic installation side effects.
- **PMC-011 [P0]** Keep passwords, keys, personal data, device dumps and sensitive captures out of public Git.
- **PMC-012 [P1]** Implement Linux-native Bash/Python execution and compatible package managers; do not assume Windows PowerShell provisioning scripts are portable.
- **PMC-013 [P2]** Export a sanitized workstation inventory and verification report.

## 15. Security, quality and maintainability
- **NFR-001 [P0]** Use least privilege and request elevation only for operations that require it.
- **NFR-002 [P0]** Provide explicit user confirmation for destructive and hazardous actions.
- **NFR-003 [P0]** Validate download sources and avoid untrusted install commands.
- **NFR-004 [P1]** Version scripts, documentation and manifests in GitHub.
- **NFR-005 [P1]** Use consistent exit codes, clear errors, help text and structured logs.
- **NFR-006 [P1]** Keep installation steps repeatable and avoid unnecessary changes.
- **NFR-007 [P1]** Document backup, rollback and manual recovery limitations.
- **NFR-008 [P1]** Maintain installation and troubleshooting documentation.
- **NFR-009 [P1]** Run authorized tests only; avoid uncontrolled network scanning or industrial operations.
- **NFR-010 [P2]** Support portable configurations on future Linux workstations.

## 16. Verification and acceptance
| Test ID | Requirement coverage | Acceptance evidence |
|---|---|---|
| T-001 | SYS-001..005 | Live-USB hardware checklist and chosen distribution |
| T-002 | APP-001..006 | Approved profile dry-run, installed package inventory |
| T-003 | COMP-001..007 | Safe disk identification and test image restore |
| T-004 | EMB-001..007 | USB serial session and one supported MCU test |
| T-005 | PLC-001..006 | Local/simulated Modbus read without physical output changes |
| T-006 | NET-001..005 | Authorized packet capture and connectivity results |
| T-007 | ELEC-001..010 | Example schematic, SPICE result and supported logic capture |
| T-008 | RAD-001..006 | Radio config backup, AF tone and receive-only SDR test |
| T-009 | RAD-007..012 | Instrument-rated RF procedures with recorded limits and calibration |
| T-010 | PMC-001..013 | Manifest parse, dry-run, approved install, rerun and verification log |
| T-011 | NFR-001..010 | Safety review, backup and recovery procedure checks |

No test is considered passed solely because an application opens; relevant functionality must be demonstrated safely.

## 17. Phased roadmap and change control
Refer to [Roadmap.md](Roadmap.md) for phases 0–7, dependencies, milestone backlog and completion gates. Requirement IDs remain stable; changes receive Git commits and version updates. Each feature progresses through **Proposed → Approved → In Progress → Installed → Verified → Complete** or is **Blocked/Deferred**.

## 18. Open decisions
1. Exact HP Pavilion model, CPU, RAM, disk, firmware and network chipsets.
2. Final Linux distribution and package availability.
3. PMC implementation, orchestration location and Linux integration capability.
4. Manifest schema (YAML/JSON/CSV), version pinning and verification format.
5. Target MCU/PLC/radio models, adapters, measurement instruments and calibration needs.
6. Default versus optional software profiles and offline-package strategy.
7. Selected repository license; the existing LICENSE file is a placeholder, not an approved license.

## 19. Initial implementation rule
This document is a scope and verification baseline, **not authorization to install all applications or operate attached hardware**. Begin with Phase 0 hardware discovery and a reviewed, non-destructive provisioning dry run.
