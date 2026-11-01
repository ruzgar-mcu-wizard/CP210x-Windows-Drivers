
# CP210x Windows Drivers

Universal Windows installation helper for Silicon Labs CP210x USB-to-UART bridge drivers.

## Overview

This repository provides the original Silicon Labs CP210x Windows driver package alongside a simple command-line installer.

Instead of manually running the vendor's graphical installer or navigating Device Manager, the included script uses Windows' built-in `pnputil` utility to install the driver directly into the Windows Driver Store.

## Supported Devices

The driver package supports the following CP210x devices:

- CP2101
- CP2102
- CP2103
- CP2104
- CP2102N
- CP2105
- CP2108
- CP2110

Device support depends on the hardware IDs included in the supplied INF file.

## Architecture Support

The installer supports:

- x86
- x64 (AMD64)
- ARM32
- ARM64

Actual architecture support depends on the included vendor driver package.

## Installation

1. Download or clone this repository.
2. Extract the files if downloaded as a ZIP archive.
3. Run `CP210x_Driver_Installer_Universal_Windows.cmd`.
4. Approve the Administrator privilege request.
5. The installer automatically registers the driver using Windows PnPUtil.

The installer executes:

```cmd
pnputil /add-driver silabser.inf /install
```

Windows automatically identifies matching devices and selects the appropriate driver.

## Files

| File | Description |
|---|---|
| `CP210x_Driver_Installer_Universal_Windows.cmd` | Universal command-line installation helper |
| `silabser.inf` | Silicon Labs driver installation information file |
| Vendor driver files | Original driver package components |

## Downloads

**Download the complete repository:**

[Download ZIP](https://github.com/ruzgar-mcu-wizard/CP210x-Windows-Drivers/archive/refs/heads/main.zip)

**Download the installer directly:**

[CP210x_Driver_Installer_Universal_Windows.cmd](https://raw.githubusercontent.com/ruzgar-mcu-wizard/CP210x-Windows-Drivers/main/CP210x_Driver_Installer_Universal_Windows.cmd)

## Requirements

- Windows
- Administrator privileges
- Windows PnPUtil
- The complete Silicon Labs driver package

## Disclaimer

This is an independent installation helper project.

Silicon Labs is the original developer of the CP210x hardware and its associated drivers. This repository is not affiliated with or endorsed by Silicon Labs.

All original driver copyrights and trademarks belong to their respective owners.
