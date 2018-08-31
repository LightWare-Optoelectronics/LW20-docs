# Firmware change log

<!-- !> Please note that the SF20 and LW20 are functionally the same device. This document will refer to both as the LW20. -->

> Firmware of the LW20 can be upgraded using the tool found at http://support.lightware.co.za/LightWareUpgrader-1.8.0.rar.

## 1.2.3

*Features*
- Improved EMC characteristics for unshielded SF20 units in the 24Mhz range.

## 1.2.2

*Notes*

Internal changes that do not have any performance or functionality impact.

## 1.2.1

*Bug fix*
- Fixed I2C legacy output mode (Reading 2 btyes from register 0) that would fail to output the correct distance at less than 2.56 m.

## 1.2.0

*Features*
- Improved EMC characteristics for unshielded SF20 units.

## 1.1.3

*Features*
- New more robust I2C implementation.
- Command to select interface boot mode.
- Legacy banner mode.

## 1.1.2

*Bug fixes*
- Reading/Writing reserved command IDs in LWNX mode no longer causes a crash.

## 1.1.1

*Bug fixes*
- Shifted LWNX command IDs to match original implementation.

## 1.1.0

*Features*
- Added LWNX command set.

## 1.0.2

*Bug fixes*
- Raised APD limit for better behaviour with certain background light conditions.

## 1.0.1

*Bug fixes*
- Fixed noise counter erroneously reporting 0.

## 1.0.0

*Notes*

Initial release.