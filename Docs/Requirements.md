# Linux-Tech-Toolkit — Requirements

**Status:** Draft 0.2 · **Date:** 2026-11-19

## 1. Purpose
Provide a portable, free-software-first Linux engineering workstation for computer servicing, microcontroller/MPU development, PLC experiments, network diagnostics, amateur radio and electronic debugging.

## 2. Constraints
- **REQ-001** All baseline software must be free to use; prefer open-source licensing.
- **REQ-002** The workstation must provide a graphical desktop and full terminal access.
- **REQ-003** The configuration should work offline for common diagnostic tasks after initial setup.
- **REQ-004** Hardware-specific and vendor-specific limitations must be documented.
- **REQ-005** Installation must not depend on HP OEM applications.
- **REQ-006** Record installed package versions and provide reproducible setup instructions.

## 3. Functional requirements
### Computer servicing
- **REQ-101** Identify disks, partitions, filesystem types and SMART health.
- **REQ-102** Create and restore disk images with verification procedures.
- **REQ-103** Prepare Linux and Windows installation/recovery media.
- **REQ-104** Support HDD overwrite and SSD sanitize workflows using drive-appropriate methods, with explicit target confirmation and warnings.

### Embedded systems
- **REQ-201** Provide C/C++, Python, Git and a code editor.
- **REQ-202** Support USB serial terminals, firmware flashing and supported SWD/JTAG debugging.
- **REQ-203** Provide documented Arduino, Teensy and Raspberry Pi workflows.

### PLC / industrial
- **REQ-301** Support laboratory PLC programming/simulation using free tools.
- **REQ-302** Support Modbus TCP and RTU testing, including RS485 adapters.
- **REQ-303** Use electrically isolated interfaces where appropriate; no direct connection to hazardous industrial voltages.
- **REQ-304** Do not treat experimental PLC software as a validated safety controller.

### Networking
- **REQ-401** Capture and inspect network traffic.
- **REQ-402** Support host discovery, port diagnostics, latency and throughput testing on authorized networks.
- **REQ-403** Support SSH and remote serial console workflows.

### Radio and electronics
- **REQ-501** Support CHIRP for compatible amateur radios and appropriate programming cables.
- **REQ-502** Support digital signal capture and protocol decoding using compatible analyzers.
- **REQ-503** Allow optional SDR experimentation.

## 4. Nonfunctional requirements
- **REQ-601** Favor a lightweight desktop suitable for older hardware.
- **REQ-602** Separate user data, configuration, logs and scripts.
- **REQ-603** Include backup and rollback procedures before significant changes.
- **REQ-604** Document permission requirements for serial, USB and packet capture.
- **REQ-605** Never automatically erase disks, flash firmware or alter PLC outputs without explicit user selection and confirmation.

## 5. Proposed platform
Linux Mint XFCE is the initial candidate; Debian XFCE is an alternative. Final selection depends on the HP Pavilion model, CPU architecture, RAM, storage, firmware and device compatibility.

## 6. Acceptance criteria
1. Boot Linux and use both desktop and terminal.
2. Identify an attached external drive without modifying it.
3. Open a USB serial console with a compatible device.
4. Capture packets on an authorized test network.
5. Run a local Modbus simulator/client test.
6. Save and restore a noncritical test image.
7. Reproduce the documented installation on a second machine or VM.

## 7. Open decisions
- Exact laptop model, RAM, disk type, CPU architecture and network chipset.
- Preferred distribution after live-USB hardware testing.
- Target PLC manufacturers and protocols.
- Radio models, MCU families and external debugging interfaces.
- Whether a second network interface and powered SATA dock are needed.

## 8. Full capability scope and phased delivery

All capabilities below are in project scope; inclusion does not authorize immediate installation or hardware operation. Priorities and phases are provisional and may be revised.

| Phase | Priority | Scope |
|---|---|---|
| 0 | Critical | Hardware inventory, live-USB compatibility, safety, requirements |
| 1 | Critical | Linux base, SSH, Git, Bash/Python, PMC bootstrap |
| 2 | High | Disk health, partitioning, imaging, recovery, external storage |
| 3 | High | MCU/MPU development, serial adapters, Arduino, Teensy, Raspberry Pi, debug probes |
| 4 | High | Network troubleshooting, PLC simulation, Modbus TCP/RTU |
| 5 | Medium | Circuit schematics, PCB design, SPICE, digital logic, logic analysis, enclosure CAD |
| 6 | Medium | CHIRP, audio-frequency generation/analysis, SDR reception, antenna testing |
| 7 | Later | Calibrated RF generation, transmitter power/deviation, receiver sensitivity, advanced automation |

### Electronics design and simulation
- **ELEC-001** Create and maintain schematics, component libraries and PCB layouts.
- **ELEC-002** Support analog/SPICE simulation and digital logic simulation.
- **ELEC-003** Support MCU/circuit co-simulation where supported by selected software.
- **ELEC-004** Produce PCB fabrication outputs and support 3D mechanical/enclosure design.
- **ELEC-005** Capture, decode and save digital logic measurements.
- **ELEC-006** Evaluate KiCad, Qucs-S, ngspice, SimulIDE, Logisim Evolution, PulseView/sigrok and FreeCAD as candidate tools.

### AF and RF testing
- **RF-001** Generate selectable AF tones and sweeps with suitable audio hardware.
- **RF-002** Analyze recorded audio waveforms, frequencies and distortion within instrument limits.
- **RF-003** Receive, display and log RF spectrum and demodulated signals with compatible SDR hardware.
- **RF-004** Support RF carrier frequency and power measurement only with suitably protected and calibrated instruments.
- **RF-005** Support RF signal generation and receiver sensitivity tests only with compatible signal generators and controlled connections.
- **RF-006** Support antenna SWR/impedance and filter measurements with compatible VNAs.
- **RF-007** Log frequency, level, modulation, instrument model, calibration status and test results.
- **RF-008** Require dummy-load, attenuation, input-limit, licensing and electrical safety checks for applicable RF procedures.

### Application catalog and lifecycle
- **APP-001** Maintain a catalog with application, purpose, license, official source, version, supported OS, profile, priority, dependencies and verification test.
- **APP-002** Distinguish candidate, approved, installed, configured, tested, failed and deprecated states.
- **APP-003** Support selectable installation profiles and dependency ordering.
- **APP-004** Detect existing packages and avoid unnecessary changes.
- **APP-005** Prefer distribution package managers; verify authenticity of downloaded installers and record provenance.
- **APP-006** Support upgrades, removal, configuration backups and offline packages where feasible.

### PMC provisioning integration
- **PMC-001** PMC shall consume versioned Linux-Tech-Toolkit requirements and machine-readable application manifests.
- **PMC-002** PMC shall inspect hardware and OS compatibility before planning actions.
- **PMC-003** PMC shall offer a dry-run plan showing installations, changes, dependencies, downloads, privileges and risks.
- **PMC-004** PMC shall execute approved phases in dependency order, logging each action and its outcome.
- **PMC-005** PMC shall support resume/retry and idempotent operations, with recovery guidance for failures.
- **PMC-006** PMC shall verify installed versions, required configuration and acceptance tests after provisioning.
- **PMC-007** PMC shall never silently erase disks, flash firmware, transmit RF, alter PLC outputs, or make other hazardous changes.
- **PMC-008** PMC shall keep secrets, credentials, captures, firmware dumps and machine-specific sensitive data out of the public repository.
- **PMC-009** PMC shall use Linux-native Bash/Python and supported package managers on the laptop; Windows provisioning procedures must not be assumed portable.
- **PMC-010** PMC shall support incremental updates when requirements, priorities or supported hardware change.

## 9. Requirements-to-delivery workflow

1. Define or revise requirement with stable ID, priority, dependencies and acceptance test.
2. Approve the application or hardware tool and record its compatibility and license.
3. Assign a roadmap phase; no calendar deadline is assumed.
4. Generate and review a PMC dry-run provisioning plan.
5. Back up relevant configuration; execute approved non-destructive installation steps.
6. Run verification tests and record results, versions and outstanding issues.
7. Update documentation, manifests and scripts through GitHub commits.

## 10. Provisioning boundaries and open decisions

PMC integration is a planned architecture, not an implemented Linux installer. It may require new Linux-native components. Confirm HP Pavilion specifications, target Linux distribution, application sources, hardware adapters, instrument calibration needs and PMC's existing implementation before enabling automation. All installation and device-control operations require explicit review of their effects.
