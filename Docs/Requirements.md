# Linux-Tech-Toolkit — Requirements

**Status:** Draft 0.1 · **Date:** 2026-11-19

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
