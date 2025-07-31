# Homebrew Automation for macOS MDM

Validated on Jamf with standard user accounts – Tools for 2025 deployments coming soon.

This repository provides scripts and resources to automate the use of [Homebrew](https://brew.sh) in macOS environments managed via MDM platforms such as Jamf Pro or Mosyle. These scripts are designed to work with standard (non-admin) user accounts, using a local admin defined at deployment time.

---

## Deployment Flow

The complete process is structured into three stages:

1. **Homebrew Deployment**  
   Deploy the official Homebrew `.pkg` to target machines (Apple Silicon or Intel) using your MDM system.

2. **Update Script**  
   A script that:
   - Repairs permissions on Homebrew folders  
   - Updates Homebrew and installed apps (casks and formulas)  
   - Handles specific edge cases (e.g., pgAdmin conflicts)

3. **App Installation Script**  
   A modular script to install specific apps via Homebrew casks, triggered via MDM using parameters.

---

## Compatibility

- macOS Ventura and newer  
- Apple Silicon (`arm64`) and Intel (`x86_64`)  
- Tested with:
  - Jamf Pro (standard user accounts)  
  - Homebrew installed at `/opt/homebrew` or `/usr/local`  

---

## Warnings

- Requires a local admin user passed as parameter `$5`.
- Scripts temporarily add the admin to the `wheel` group to allow privileged operations. This is reverted after execution.
- Permissions on Homebrew directories will be reassigned to the admin user to ensure operability with standard users.
- Do not use on BYOD or unmanaged devices.

Test everything in staging before deployment.

---

## Coming Soon

- `update_homebrew.sh` – update tools and cleanup
- `install_app.sh` – install specific cask via parameter
- `README_examples.md` – with sample use in Jamf Pro and Mosyle

---

MIT License
