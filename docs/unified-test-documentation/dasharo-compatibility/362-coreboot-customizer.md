# Dasharo Compatibility: DMI editing tool

## DMI001.001 Change the UUID

**Test description**

The Dasharo Configuration Utility tool is a part of the Dasharo Tools Suite.
This test case verifies that the UUID encoded in the DMI table of an
image can be changed using our utility.

**Test configuration data**

1. `FIRMWARE` = Dasharo

**Test setup**

1. Proceed with the
    [Generic test setup: firmware](../generic-test-setup.md#firmware).
1. Download [Dasharo Configuration Utility](https://github.com/Dasharo/dcu)

**Test steps**

1. Run `./dcu smbios -u 96bcfa1a-42b4-6717-a44c-d8bbc18cbea4
coreboot.rom`
1. Flash the `coreboot.rom` file onto the platform.
1. Power on the DUT.
1. Examine the DMI tables with `dmidecode`.
1. Note the results.

**Expected result**

The UUID of the platform should be `96bcfa1a-42b4-6717-a44c-d8bbc18cbea4`, just
as we had set it.

## DMI002.001 Change the serial number

**Test description**

This test case verifies that the serial number encoded in the DMI table of an
image can be changed using our utility.

**Test configuration data**

1. `FIRMWARE` = Dasharo

**Test setup**

1. Proceed with the
    [Generic test setup: firmware](../generic-test-setup.md#firmware).
1. Download [Dasharo Configuration Utility](https://github.com/Dasharo/dcu)

**Test steps**

1. Run `./dcu smbios -s D01234567 coreboot.rom`
1. Flash the `coreboot.rom` file onto the platform.
1. Power on the DUT.
1. Examine the DMI tables with `dmidecode`.
1. Note the results.

**Expected result**

The serial number of the platform should be `D01234567`, just as we had set it.

## DMI003.001 Change the bootsplash logo

**Test description**

This test case verifies that the bootsplash logo of an image can be changed
using our utility.

**Test configuration data**

1. `FIRMWARE` = Dasharo

**Test setup**

1. Proceed with the
    [Generic test setup: firmware](../generic-test-setup.md#firmware).
1. Download [Dasharo Configuration Utility](https://github.com/Dasharo/dcu)

**Test steps**

1. Run `./dcu logo -l ./logo.svg`
1. Flash the `coreboot.rom` file onto the platform.
1. Power on the DUT.
1. Verify the bootsplash logo.

**Expected result**

The bootsplash logo should now be your image of choice placed under ./logo.svg.
