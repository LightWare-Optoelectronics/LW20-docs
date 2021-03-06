# Firmware change log

## Upgrading

> NOTE: The Upgrader tool only supports Windows at this time.

1. Download the LightWare Upgrader tool here: http://support.lightware.co.za/LightWareUpgrader-1.26.0.rar
2. Unzip the downloaded file to a location on your PC.
3. Run the file `LightWareUpgrader.exe` in the unzipped folder.
4. Connect your LightWare device via USB to your PC.
5. Click the COM port that appears.
6. If the device is not the latest version you can click the `Upgrade` button to begin the process.
7. Wait until the upgrade has completed successfully and click `OK`.

## 1.6.4

*Fixes*
- Noise output has been corrected.

## 1.6.3

*Changes*
- Servo output is disabled when using Pixhawk compatibility mode.

## 1.6.2

*Changes*
- Slightly improved performance in long range conditions.
- Legacy distance command now defaults to using the median filter.

*Fixes*
- Statistics waveform streaming now outputs final bucket correctly.

## 1.6.0

*Changes*
- Downgrading firmware is now limited to a minimum of version 1.6.0. Trying to downgrade below 1.6.0 will results in the [16. Stage firmware] command displaying the -6 error code.

*Fixes*
- Downgrading firmware will no longer cause the device to lose critical parameter settings that were modified in a higher version of the firmware.

## 1.5.1

*Features*
- Added new optional start-up communication mode that will default to serial mode and not display the usual first MMI message.

## 1.5.0

*Features*
- Added a mode for fast unfiltered data output with readings at 20 kHz.

## 1.4.3

*Changes*
- Minimized power draw during start up.

## 1.4.2

*Changes*
- Improved EMC characteristics for unshielded SF20 units.

## 1.4.1

*Changes*
- Increased soft start delay for staged power draw.

## 1.4.0

*Changes*
- Increased soft start delay for staged power draw.

## 1.3.1

*Fixes*
- Servo output was accidentally disabled in `1.3.0`, this has be re-enabled.

## 1.3.0

*Features*
- Added Pixhawk I2C compatibility mode.

## 1.2.3

*Changes*
- Improved EMC characteristics for unshielded SF20 units in the 24Mhz range.

## 1.2.2

*Changes*
- Internal changes that do not have any performance or functionality impact.

## 1.2.1

*Fixes*
- Fixed I2C legacy output mode (Reading 2 bytes from register 0) that would fail to output the correct distance at less than 2.56 m.

## 1.2.0

*Changes*
- Improved EMC characteristics for unshielded SF20 units.

## 1.1.3

*Features*
- New more robust I2C implementation.
- Command to select interface boot mode.
- Legacy banner mode.

## 1.1.2

*Fixes*
- Reading/Writing reserved command IDs in LWNX mode no longer causes a crash.

## 1.1.1

*Fixes*
- Shifted LWNX command IDs to match original implementation.

## 1.1.0

*Features*
- Added LWNX command set.

## 1.0.2

*Fixes*
- Raised APD limit for better behaviour with certain background light conditions.

## 1.0.1

*Fixes*
- Fixed noise counter erroneously reporting 0.

## 1.0.0

*Changes*
- Initial release.