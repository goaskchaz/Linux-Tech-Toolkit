# Linux-Tech-Toolkit — System Architecture

**Version:** 0.1 draft  
**Date:** 2026-11-19  
**Status:** Proposed architecture; not implemented

## 1. Purpose and boundaries
Linux-Tech-Toolkit (LTT) is a versioned engineering-workstation specification, application catalog, test suite and collection of Linux-native scripts. Provisioning Management Catalog (PMC) is the proposed orchestration system that consumes approved LTT manifests and provisions a target machine. LTT must remain usable manually without PMC.

**Source of truth:** LTT GitHub repository for requirements, application metadata, profiles, procedures and scripts. PMC maintains execution state and machine-specific inventories, which must not be committed to the public repository if sensitive.

## 2. Components
| Component | Responsibility |
|---|---|
| Requirements | Stable IDs, scope, priority, dependencies, acceptance criteria |
| Application catalog | Names, licenses, sources, versions, install methods, hardware needs |
| Installation profiles | Core, Computer, MCU, PLC, Network, Electronics, Radio/RF |
| Hardware inventory | OS/architecture, CPU, RAM, disks, adapters, peripherals |
| Provisioning planner | Dependency resolution, compatibility checks, dry-run change plan |
| Executor | Approved Linux-native Bash/Python commands and package managers |
| Verifier | Package checks, configuration checks, safe acceptance tests |
| Reporting | Execution logs, versions, results, warnings, recovery instructions |

## 3. Integration contract (proposed)
A future machine-readable manifest should identify:
- `id`, `name`, `phase`, `priority`, `profile`, `license`
- `supported_distributions`, `architectures`, `minimum_resources`
- `source_url`, `install_method`, `package_name`, `dependencies`
- `configuration_steps`, `verification`, `rollback`, `risk_level`

Manifest format (YAML/JSON/CSV) is **TBD**; examples are illustrative, not an implemented interface. Avoid ambiguous floating download URLs and unverified third-party installers. Pin versions or record approved version constraints where feasible.

## 4. Provisioning workflow
```text
LTT Requirements + Catalog + Profiles
                 |
          PMC reads manifests
                 |
       Hardware / OS preflight
                 |
        Resolve dependencies
                 |
       Show dry-run change plan
                 |
      User approves safe actions
                 |
      Backup relevant settings
                 |
        Download + verify source
                 |
        Install + configure
                 |
         Verify + record results
                 |
      Update inventory and issues
```

## 5. Operational modes
- **Inspect:** collect read-only machine inventory.
- **Plan:** display actions, privileges, download sizes if known, dependencies and risks; make no changes.
- **Apply:** perform approved package and configuration changes.
- **Verify:** run non-destructive checks and document results.
- **Repair/Resume:** retry idempotent steps and report partial failures.
- **Export:** create sanitized inventory and test reports.

## 6. Safety architecture
- Default to read-only operations and explicit dry-run.
- Separate package provisioning from device operations (disk erase, imaging restore, firmware flashing, PLC output changes and RF transmission).
- Require distinct, explicit confirmation for destructive or hazardous device actions; PMC must never perform them as side effects of installing a profile.
- Require authorized network scope for scans and packet capture.
- Use appropriate electrical isolation, voltage matching, RF dummy loads, attenuation and input protection.
- Protect secrets and machine-specific information; never commit credentials, captures or personal data.
- Limit elevated privileges to specific operations; never run an entire interactive GUI as root.
- No automatic RF transmission or PLC control in initial implementation.

## 7. Reproducibility and failure handling
- Scripts should be idempotent, logged, versioned, and return meaningful exit codes.
- Use distribution-supported package managers first (APT on Debian/Mint); support additional packaging only after review.
- Validate downloads via trusted signatures/checksums when provided; record provenance.
- Store local installation state and backup references outside Git.
- A failure stops dependent steps, preserves logs and permits controlled retry.
- Not all changes are automatically reversible: document restore points and manual recovery.

## 8. Proposed repository boundaries
```text
Linux-Tech-Toolkit/
  Docs/          Requirements, Architecture, Roadmap, Installation, Hardware, Safety, Testing
  Applications/  Catalog and profile manifests (future)
  Setup/         Linux bootstrap, installers, verifiers (future)
  Computer/ MCU/ PLC/ Network/ Radio/ Electronics/
  Scripts/       Reusable Bash and Python diagnostics
```

PMC implementation and its source code should remain in the separate PMC project. The cross-project interface is a planned integration; existing PMC Linux support has not been verified.

## 9. Architecture decisions pending
1. Confirm Pavilion hardware and Linux distribution.
2. Inspect current PMC code and decide whether it orchestrates locally, remotely via SSH, or both.
3. Select manifest format, schema and validation rules.
4. Choose secure artifact and log locations.
5. Define automated acceptance-test runner and rollback limits.
6. Approve which capabilities are installed by default versus optional.
