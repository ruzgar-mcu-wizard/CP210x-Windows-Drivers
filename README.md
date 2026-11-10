# CP210x Windows Drivers

A Windows installation helper for the Silicon Labs CP210x USB-to-UART driver package.

This repository includes the vendor driver files and a small command-line installer that uses Windows' built-in Plug and Play utility, `pnputil`.

## What it does

The installer adds the supplied INF package to the Windows Driver Store and asks Windows to install it for matching devices.

It runs:

```cmd
pnputil /add-driver silabser.inf /install
```

Windows handles device detection and matches connected hardware against the hardware IDs and driver sections in the INF file.

## Supported devices

The included driver package lists support for CP210x-family USB-to-UART devices, including:

- CP2101
- CP2102
- CP2103
- CP2104
- CP2102N
- CP2105
- CP2108
- CP2110

The exact devices supported are determined by the hardware IDs in the included `silabser.inf` file.

## Architecture support

The package includes driver support for the following Windows architecture families:

- x86
- x64 (AMD64)
- ARM32
- ARM64

Actual compatibility depends on the architecture-specific driver files and sections present in the supplied vendor package.

## Installation

1. Download the repository or use the ZIP download linked below.
2. Extract the archive if necessary.
3. Run `CP210x_Driver_Installer_Universal_Windows.cmd`.
4. Approve the Administrator permission prompt.
5. Allow PnPUtil to add and install the driver package.

The installer requires an elevated Windows session because adding a driver to the Driver Store requires administrator permissions.

### Manual installation

You can also install the INF package from an elevated Command Prompt:

```cmd
pnputil /add-driver silabser.inf /install
```

## Repository contents

| File | Purpose |
| --- | --- |
| `CP210x_Driver_Installer_Universal_Windows.cmd` | Command-line installation helper |
| `silabser.inf` | Silicon Labs driver installation information |
| Vendor driver files | Driver package components supplied with the repository |

Keep the INF file and its associated driver files together when installing.

## Downloads

- [Download the complete repository ZIP](https://github.com/ruzgar-mcu-wizard/CP210x-Windows-Drivers/archive/refs/heads/main.zip)
- [Browse the repository](https://github.com/ruzgar-mcu-wizard/CP210x-Windows-Drivers)

## Requirements

- A supported version of Windows.
- Administrator permissions.
- The included Silicon Labs driver package.
- Windows PnPUtil (included with supported Windows versions).

## Troubleshooting

**The device is still listed as unknown**

- Disconnect and reconnect the USB device.
- Check Device Manager for the device's hardware ID.
- Confirm that the hardware ID is covered by the supplied INF file.
- Check whether Windows reports a driver installation error.

**The installer cannot find the INF file**

- Run the script from the extracted repository directory.
- Keep `silabser.inf` and its associated files in the expected package layout.
- Do not run the script from inside an archive preview.

**PnPUtil reports that no matching devices were installed**

The driver package may have been added successfully even if no currently connected device matched it. Connect the relevant CP210x device and check Device Manager.

## Disclaimer

This is an independent installation helper and is not affiliated with or endorsed by Silicon Laboratories.

Silicon Laboratories is the developer of the CP210x hardware and vendor driver package. All original driver copyrights and trademarks belong to their respective owners.
