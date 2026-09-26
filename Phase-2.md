# Phase II

## Pre-Upgrade Operational Checklist

* **Data Backup:** Completed. All critical user files, photos, and documents were exported across two separate external USB storage devices to ensure redundancy. Web-based configurations and browser profiles were synchronized via cloud accounts to prevent data loss.
* **PC Health Check:** Completed. Device flagged as completely incompatible with official Windows 11 specifications.
* **TPM 2.0 Status:** Isolated. Hardware module is not detected on this device.
* **Secure Boot Status:** Supported by system firmware, but PCR7 platform configuration register binding is unsupported due to the missing hardware security architecture.
* **Power Connection:** Secured. Laptop is plugged into a dedicated AC power source to eliminate battery depletion risks.

## Installation & Deployment Notes

**Resources/Tools utilized:** Patriot P210 512GB SATA 2.5" SSD (purchased), SanDisk Cruzer USB flash drive (purchased), Rufus, Windows 11 ISO, InsydeH2O Setup Utility, Norton Antivirus (optional).

| Patriot P210 512GB SSD | SanDisk Cruzer USB Flash Drive |
| :---: | :---: |
| <img src="https://github.com/user-attachments/assets/90e5061f-6213-412b-8dbc-ad717f854fce" width="250" /> | <img src="https://github.com/user-attachments/assets/2cfe4701-21b5-4c02-a5f8-16811d287682" width="250" /> |

---

## Technical Execution & Deployment Procedures

* **Method Used:** USB Bootable Media (compiled with MBR partition scheme via Rufus to bypass TPM 2.0 and CPU restrictions).
* **Observations During Install:** The InsydeH2O firmware required Legacy Support enabled and Secure Boot disabled to successfully locate and execute the bootloader on the MBR-formatted Patriot SSD.
* **Post-Deployment USB Media Remediation:** The deployment process left the SanDisk flash drive partitioned with hidden boot volumes. Restoring the media back to its full capacity required a manual volume purge and file system re-provisioning (NTFS format) via Disk Management.

## Workflow

### Stage 1: Physical Disassembly & Storage Remediation

The upgrade started by unboxing and inspecting the new Patriot P210 512GB SATA SSD to make sure the physical pins were clean and undamaged. Once the drive checked out, I flipped the laptop over to get inside the chassis. Using a precision screwdriver, I removed the bottom casing screws and carefully unclipped the plastic trim to expose the motherboard layout. Never force the device to open; sometimes there are hidden screws within the assembly. Check carefully and utilize online resources on the device to locate hidden fasteners.

With the internals accessible, I carefully disconnected the SATA ribbon cable from the slow, failing mechanical drive. I swapped the old drive out of its mounting caddy, screwed the new Patriot SSD into place, and reattached the ribbon cable. After making sure the connection was solid, I seated the drive back into the primary bay and snapped the laptop chassis back together, ensuring all pieces were back in place.

**Legacy Drive Identification:**

<img width="300" alt="Legacy WD Blue 500GB HDD" src="https://github.com/user-attachments/assets/8c0eee9c-f336-49ec-905c-8289f19f98fc" />

### Stage 2: Bootable Installation Media Creation & Firmware Access

With the hardware installed, it was time to build the bootable installer. On my main machine, I used Rufus to flash the Windows 11 ISO onto a SanDisk Cruzer flash drive. I specifically chose an MBR partition layout during configuration so the image would line up with the laptop's older architecture. I plugged the flash drive into the laptop, powered it on, and tapped F10 to jump straight into the InsydeH2O Setup Utility before Windows could try to boot.

**Firmware Configuration Interface (InsydeH2O Setup Utility):**

<img width="800" alt="InsydeH2O Setup Utility Firmware Configuration" src="https://github.com/user-attachments/assets/bf811eaa-91d2-4117-86d1-fd27ce02bb51" />

Inside the BIOS settings, I navigated over to the system configuration menu, turned Legacy Support On, and verified that Secure Boot toggled itself Off. This quick firmware adjustment was what allowed the older motherboard to read the MBR storage layout without throwing an error. I saved the settings and let the system reboot. The laptop picked up the SanDisk flash drive immediately and installation began.

## Challenges Encountered 

Rufus settings were wrong in this part of installation. GPT partition scheme needed to be MBR partition scheme to match the older architecture. The Target system was changed from UEFI to BIOS/Legacy mode so that the InsydeH2O firmware could read the MBR partition scheme on boot. Additionally, Secure boot status needed to be disabled. Without being changed, the above "Fail" error was received.

| Image 1 | Image 2 |
| :---: | :---: |
| <img src="https://github.com/user-attachments/assets/c3498c4b-aa6b-4ef1-b27f-65ee7eec6f95" width="350" /> | <img src="https://github.com/user-attachments/assets/de303b90-59f1-46b5-afe1-b7712206afa2" width="350" /> |

### Stage 3: Post-Installation Validation & Storage Verification

Once the installation finished and I landed on the fresh Windows 11 desktop, I pulled up the advanced storage settings to run a quick audit. The Patriot SSD was fully recognized, properly aligned, and running cleanly; everything looked great!

<img width="1032" height="311" alt="image" src="https://github.com/user-attachments/assets/dadee4ef-95cc-4f85-bf7a-9ed57e985d31" />







