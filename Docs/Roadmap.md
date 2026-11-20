# Linux-Tech-Toolkit — Development Roadmap

**Version:** 0.1 draft  
**Date:** 2026-11-19  
**Scheduling model:** Dependency-driven phases, no committed calendar dates.

## 1. Prioritization
- **P0 Critical:** prerequisites, safety and basic functionality.
- **P1 High:** core utility and development capabilities.
- **P2 Medium:** useful laboratory capabilities after baseline is stable.
- **P3 Later:** advanced, instrument-dependent and calibration-intensive features.

A phase advances when its acceptance criteria pass, not merely when packages install. Reprioritize at each review.

## 2. Delivery phases

| Phase | Priority | Scope | Prerequisite | Completion gate |
|---|---|---|---|---|
| 0 Discovery | P0 | Hardware inventory, Linux live-USB compatibility, safety, requirements | None | Hardware documented; distribution selected; backup plan approved |
| 1 Foundation | P0 | Linux, desktop, CLI, SSH, Git, Python, package management, PMC bootstrap concept | 0 | Boots reliably; network and USB work; basic package verification passes |
| 2 Computer Service | P1 | SMART, partitioning, imaging, restoration, recovery USB | 1 | Non-destructive disk inspection and test image restore verified |
| 3 MCU / Embedded | P1 | Arduino, Teensy, Raspberry Pi, UART, SWD/JTAG | 1 | Serial console and one supported firmware workflow verified |
| 4 Network / PLC | P1 | Wireshark, Nmap, iperf3, OpenPLC, Modbus TCP/RTU | 1; adapters as needed | Authorized packet capture and local Modbus test pass |
| 5 Electronics Design | P2 | KiCad, Qucs-S, ngspice, SimulIDE, Logisim, PulseView, FreeCAD | 1; peripherals for capture | Example schematic, simulation and logic capture verified |
| 6 Radio / AF / SDR | P2 | CHIRP, audio tones, audio analysis, SDR reception, NanoVNA | 1; compatible devices | Audio test and safe receive-only SDR/antenna workflow verified |
| 7 Advanced RF / Automation | P3 | Calibrated RF generation, receiver sensitivity, power/deviation measurement, richer PMC orchestration | 6; calibrated instruments | Safe, documented and repeatable instrument tests verified |

Phases 2–6 may proceed independently once Phase 1 is complete, subject to hardware, budget and safety.

## 3. Per-feature workflow
1. Define requirement and acceptance test.
2. Record application/hardware candidate, free license, source and compatibility.
3. Assign phase, priority and dependencies.
4. Approve proposed changes and update manifest.
5. Build a dry-run provisioning plan.
6. Install/configure in a test environment.
7. Run tests and document outcomes.
8. Merge tested scripts and documentation into GitHub.
9. Revisit requirements and reprioritize the backlog.

## 4. Initial milestone backlog
- **M0.1** Capture Pavilion model, CPU, RAM, storage, BIOS/UEFI, network/USB chipsets.
- **M0.2** Test Mint XFCE and/or Debian XFCE live media.
- **M0.3** Define safe backup and rollback approach.
- **M1.1** Approve base packages and minimal installation profile.
- **M1.2** Decide PMC-to-LTT manifest contract and test a dry-run parser.
- **M1.3** Implement safe install and verification scripts.
- **M2.1** Validate a spare external disk imaging and restoration workflow.
- **M3.1** Validate a USB UART console and a supported MCU board.
- **M4.1** Validate network and Modbus loopback tests.
- **M5.1** Validate circuit schematic and SPICE simulation.
- **M6.1** Validate receive-only SDR and audio test procedures.

## 5. Progress tracking
Each work item should record: ID, owner (if assigned), priority, phase, dependency, status, verification evidence, GitHub commit or issue, and next action.

Statuses: **Proposed → Approved → In Progress → Installed → Verified → Complete**; alternatives **Blocked** or **Deferred**.

## 6. Scope controls
- Catalog inclusion is not approval to install.
- External hardware purchases are optional and separately approved.
- Advanced RF tests require proper instruments and safety procedures.
- Vendor PLC tools may be proprietary; record exceptions instead of assuming free compatibility.
- Avoid target dates until hardware readiness and workload are known.

## 7. Next decision
Complete Phase 0 hardware discovery before implementing any automated Linux provisioning.
