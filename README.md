# Linux-Tech-Toolkit

A collection of free Linux-based tools, scripts, and configurations for computer maintenance, disk recovery, microcontroller development, PLC diagnostics, network analysis, amateur radio, and electronics testing.

## Project goals
- Repurpose an older HP Pavilion laptop into a portable Linux engineering workstation.
- Support both graphical desktop and command-line workflows.
- Prefer free and open-source software, documenting any vendor-specific exceptions.
- Make setup reproducible and useful offline once tools are installed.

## Work areas
| Area | Scope |
|---|---|
| Computer | Disk health, partitioning, imaging, operating-system recovery |
| MCU | Arduino, Teensy, Raspberry Pi, firmware flashing and serial consoles |
| PLC | OpenPLC experimentation, Modbus TCP/RTU diagnostics |
| Network | Authorized packet capture, network discovery, throughput testing |
| Radio | CHIRP programming, digital modes, SDR |
| Electronics | Logic analysis, signal capture and protocol decoding |

## Documentation
- [Requirements](Docs/Requirements.md) — functional and safety requirements
- [Software Catalog](Docs/Software-Catalog.md) — free tools and official project sites
- [Hardware](Docs/Hardware.md) — laptop inventory and external interfaces

## Planned structure
`Setup/` for installation scripts and package manifests; `Computer/`, `MCU/`, `PLC/`, `Network/`, `Radio/`, and `Electronics/` for domain procedures; `Scripts/` for reusable Bash and Python utilities.

## Getting started
1. Identify the exact Pavilion model, CPU, RAM, storage and network adapters.
2. Back up existing data.
3. Test a Linux Mint XFCE or Debian XFCE live USB for hardware compatibility.
4. Review the requirements and select software from the catalog.
5. Install and validate tools incrementally.

## Safety
Disk wiping, firmware flashing and PLC I/O can cause permanent data loss or hardware damage. Verify device identity, keep backups, use correctly rated and isolated adapters, and require explicit confirmation for destructive operations.

## Status
Initial documentation. No installer scripts or hardware validation have been completed.
