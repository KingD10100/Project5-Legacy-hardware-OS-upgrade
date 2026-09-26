# Project 5: Legacy Hardware & OS Upgrade

## Overview

This project involved troubleshooting severe endpoint latency on a legacy laptop, executing a physical storage upgrade to resolve disk saturation, and deploying Windows 11 on unsupported hardware to eliminate an End-of-Life operating system vulnerability. It integrated multiple topics, including:

* Computer Architecture & Hardware Remediation
* Operating System Deployment & Provisioning
* Firmware & BIOS/UEFI Configuration
* Endpoint Security & Lifecycle Compliance
* Storage Management & File Systems
* Data Preservation & Redundancy

### Project Deliverables

Key technical milestones achieved across the project lifecycle:
*  Identified hardware bottlenecks using system health metrics
*  Executed a fault-tolerant, redundant data backup
*  Performed physical hardware disassembly and a 2.5" SATA SSD replacement
*  Built custom bootable media using Rufus to bypass TPM 2.0 and CPU checks
*  Reconfigured UEFI/BIOS settings for legacy boot and drive execution
*  Deployed a clean installation of Windows 11
*  Restored and re-partitioned installation media using Disk Management

---

## Phase 1: Host Discovery, Baseline Assessment & Remediation Strategy

Phase 1 focused on diagnosing system performance limits, evaluating OS upgrade eligibility, auditing security baselines, and engineering the technical remediation strategy. This portion of the project incorporated key concepts from System Diagnostics, Endpoint Lifecycle Planning, and Data Protection.

### Phase Objectives

*  Establish baseline host hardware and software configurations
*  Execute PC Health Check diagnostics to isolate hardware incompatibilities
*  Assess cybersecurity risks associated with running an End-of-Life (EOL) OS
*  Implement a redundant data preservation strategy across external storage and cloud accounts
*  Engineer a technical strategy to procure replacement SSD hardware and circumvent deployment blocks

---

## Phase 2: Hardware Remediation, Firmware Configuration & OS Deployment

Phase 2 focused on physical chassis disassembly and storage replacement, bypassing hardware verification checks, reconfiguring system firmware, completing a clean operating system installation, and reclaiming deployment media. This portion of the project incorporated key concepts from Computer Hardware Remediation, Firmware Management, Operating System Deployment, and Storage Administration.

### Phase Objectives

* Disassemble the chassis and replaced the failing mechanical HDD with a 512GB SATA SSD
* Generate custom bootable Windows 11 media via Rufus to bypass TPM 2.0 and CPU restrictions
* Reconfigure InsydeH2O BIOS settings (enabled Legacy Support and disabled Secure Boot) to execute the MBR bootloader
* Execute a clean installation of Windows 11 onto the newly provisioned SSD
* Re-provision and restore the partitioned USB deployment media using Windows Disk Management

---

## Conclusion: Retrospective & Takeaways

A post-upgrade analysis covering hardware lifecycle extension, software-layer security mitigations for legacy systems, and project takeaways.
