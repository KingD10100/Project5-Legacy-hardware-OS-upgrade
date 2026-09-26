# Phase 1: Host Discovery, Baseline Assessment & Remediation Strategy

## Host Discovery & Baseline Configuration

Initial asset auditing was conducted to evaluate existing hardware capabilities and baseline device identifiers prior to technical intervention:

| System Attribute | Baseline Specification | Compliance Evaluation |
| :--- | :--- | :--- |
| **Asset Lifecycle Platform** | HP 15 Notebook PC (Vintage: ~10 Years) | Legacy OEM Chassis |
| **Compute Architecture (CPU)** | Intel Celeron N2840 @ 2.16 GHz | Failed (Unsupported architecture) |
| **Volatile Memory (RAM)** | 4.00 GB DDR3 SDRAM (3.89 GB Usable) | Met (Baseline operational limit) |
| **Non-Volatile Storage (Disk)** | 500 GB Mechanical Hard Disk Drive (HDD) | Failed Performance Baseline |
| **System Target Environment** | 64-bit Architecture / x64-based Processor | Met |
| **Device Logical Identifier** | `BC4E56C7-XXXX-XXXX-XXXX-FCD353E450B0` | System GUID Isolated |
| **OS Product Licensing ID** | `00325-80035-XXXXX-AAOEM` | Active OEM Digital License |

---

## PC Health Check Results

A diagnostic audit was executed via the official PC Health Check utility to evaluate the endpoint against Windows 11 deployment criteria:

* **TPM 2.0:** Currently not detected. Must be supported and enabled for standard deployment.
* **Processor (CPU):** Not currently supported for Windows 11.
* **Secure Boot:** Supported by hardware.
* **System Memory:** Met. 4.00 GB detected (minimum required: 4 GB).
* **Storage Capacity:** Met. 500 GB detected (minimum required: 64 GB).
* **Processor Cores:** Met. 2 physical cores detected (minimum required: 2 cores).
* **Endpoint Protection Status:** PC is monitored and protected.

---

## Pre-Deployment Analysis & Risk Assessment

* **Storage I/O Bottlenecks:** Running Windows 11 on a legacy 500 GB mechanical HDD will severely degrade performance due to severe disk utilization spikes. Modern operating systems rely heavily on Solid State Drive (SSD) high-speed random read/write cycles.
* **Architectural Limitations:** The Intel Celeron N2840 is an older dual-core mobile processor lacking modern architectural instruction sets and is omitted from Microsoft's official hardware eligibility list.
* **Memory Overhead:** 4 GB of RAM is a structural bare minimum for Windows 11, leaving zero operational overhead for user applications, background processes, or system stability.
* **Operating System Lifecycle Risk:** Microsoft officially terminated standard lifecycle support for Windows 10 on October 14, 2025. Running an End-of-Life (EOL) operating system exposes the endpoint to unmitigated zero-day vulnerabilities, unpatched exploits, and compliance non-conformity.

### Reference: Microsoft Minimum Upgrade Thresholds

According to Microsoft (n.d.), an endpoint must satisfy the following criteria for a direct operating system upgrade:

* **Processor (CPU):** 1 GHz or faster with 2 or more physical cores on an approved, compatible 64-bit architecture (generally requiring 8th Gen Intel Core / AMD Ryzen 2000 series or newer).
* **System Memory (RAM):** 4 GB minimum baseline capacity.
* **Storage Capacity:** 64 GB or larger available disk space on the primary OS volume.
* **System Firmware:** UEFI (Unified Extensible Firmware Interface) architecture with Secure Boot capability.
* **Hardware Security Module:** Trusted Platform Module (TPM) version 2.0 enabled and active.
* **Graphics & Display:** DirectX 12 compatible graphics subsystem with a WDDM 2.0 driver, paired with a high-definition (720p) display greater than 9 inches diagonally.
* **Baseline OS Version:** Device must be running Windows 10, version 2004 or later, to upgrade through Windows Update.

---

## Operational Checklist

*  **Data Backup Executed:** Exported all critical user files, photos, and documents across two separate external USB storage devices to ensure redundancy and hardware fault tolerance.
*  **Cloud Profile Synchronization:** Synchronized web-based configurations and browser profiles across individual Google user accounts, ensuring seamless cross-device accessibility and guaranteeing zero data loss post-installation.
*  **PC Health Check Completed:** Documented that the device does not meet required specifications for standard Windows 11 deployment.
*  **TPM 2.0 Status Isolated:** Confirmed hardware security module is not detected on the motherboard and is unavailable for platform binding.
*  **Secure Boot Evaluated:** Verified firmware support, noting PCR7 platform binding is unsupported due to missing hardware security architecture.
*  **Power Connection Secured:** Connected the laptop to continuous AC wall power to eliminate battery depletion risk during remediation.

---

## Technical Strategy

### Step 1: Storage Hardware Remediation Plan
The mechanical hard drive (HDD) represents the primary physical performance bottleneck. Upgrading this component is mandatory to achieve an operational baseline.
* **Action Plan:** Procure a standard 2.5-inch SATA Solid State Drive (SSD) to completely replace the legacy mechanical HDD.
* **Resource Allocation:** Procure a 256 GB or 512 GB SATA SSD ($25–$35 price point) from a reputable manufacturer to eliminate disk saturation and I/O latency.

### Step 2: Administrative Deployment Bypass Plan
Because the laptop fails official CPU generation and TPM 2.0 validation checks, the standard installation path via Windows Update is blocked.
* **Action Plan:** Leverage administrative media creation tools (Rufus) to build bootable installation media that bypasses TPM 2.0 and CPU eligibility restrictions.
* **Outcome:** Remediates the End-of-Life operating system vulnerability and extends the hardware lifecycle without requiring new computer acquisition.
