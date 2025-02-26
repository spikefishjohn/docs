# Firmware update

## Introduction

This document describes the process for updating firmware on devices running
Dasharo firmware. Some steps specific to each device will be described in their
respective documentation, but the generic process outlined here will apply to
all devices.

## Firmware Update Mode

For enhanced firmware security, Dasharo uses a number of security mechanisms to
prevent overwriting firmware. Depending on device, these may be some or all of
the following:

- SPI flash write-protection - prevents overwriting the initial bootblock and
  Verified Boot code
- SMM BIOS write protection - prevents all writes to BIOS flash memory outside
  of privileged code running in System Management Mode
- UEFI Secure Boot - in combination with Linux Kernel Lockdown, prevents direct
  access to the SPI flash controller from the OS

If you are interested, see the
[Dasharo System Features](../dasharo-menu-docs/dasharo-system-features.md)
section for more details.

To allow updating firmware by the end user, these protections must be disabled
first. To facilitate this, Dasharo has a Firmware Update Mode option that
**temporarily** disables firmware security measures for the duration of one
boot.

To enter Firmware Update Mode:

1. Enter the Setup Menu and navigate to Dasharo System Features:
![](./images/setup_menu_dsf.png)
1. Navigate to `Dasharo Security Options`:
![](./images/setup_menu_dsc.png)
1. Select `Firmware Update Mode`:
![](./images/setup_menu_fum.png)
1. When prompted, press Enter to accept. The device will reboot in Firmware
  Update Mode.
![](./images/setup_menu_fum_confirmation.png)
1. After reboot, when prompted, press the indicated key on the keyboard.
  Alternatively, to abort Firmware Update Mode, press Enter instead or simply
  wait for the timeout to expire.

Once in Firmware Update Mode, proceed with the firmware update steps outlined
in device-specific documentation.

## Firmware Update Mode flowchart

![](./images/fum_flowchart.png)
