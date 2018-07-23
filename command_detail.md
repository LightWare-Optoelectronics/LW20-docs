# Detailed command descriptions

---
## 0. Product name

A `16 byte string` indicating the product model name. This will always be `LW20` followed by a null terminator. You can use this to verify the LW20 is connected and operational over the selected interface.

|Read|Write|Persists|
|---|---|---|
| `16 byte string` | - | - |

---
## 1. Hardware version

The hardware revision number as a `uint32`.

|Read|Write|Persists|
|---|---|---|
| `uint32` | - | - |

---
## 2. Firmware version

The version of currently installed firmware represented as `4 bytes`. This can be used to identify the product for API compatibility. The [product support](/?id=product-support) section details which firmware versions this document applies to.

| 1 | 2 | 3 | 4 |
|---|---|---|---|
|Patch|Minor|Major|Reserved|

|Read|Write|Persists|
|---|---|---|
| `4 bytes` | - | - |

---
## 3. Serial number

A `16 byte string` (null terminated) of the serial identifier assigned during production.

|Read|Write|Persists|
|---|---|---|
| `16 byte string` | - | - |

---
## 7. UTF8 text message

*Serial interface only*

A null terminated ASCII string. The LW316 will send this command when it needs to communicate a human readable message.

|Read|Write|Persists|
|---|---|---|
| - | - | - |

---
## 9. User data

This command allows 16 bytes to be stored and read for any purpose.

|Read|Write|Persists|
|---|---|---|
| `16 bytes` | `16 bytes` | Yes |

---
## 10. Token

Current safety token required for performing certain operations. Once a token has been used it will expire and a new token is created. 

|Read|Write|Persists|
|---|---|---|
| `uint16` | - | - |

---
## 12. Save parameters

Several commands write to parameters that can persist across power cycles. These parameters will only persist once the `Save parameters` command has been written with the appropriate `token`. The safety token is used to prevent unintentional writes and once a successful save has completed the token will expire.

|Read|Write|Persists|
|---|---|---|
| - | `uint16` | - |

---
## 14. Reset

Writing the safety `token` to this command will restart the LW20.

|Read|Write|Persists|
|---|---|---|
| - | `uint16` | - |

---
## 16. Stage firmware

Upload firmware page.

*More detail coming soon*

|Read|Write|Persists|
|---|---|---|
| `uint32` | `130 bytes` | - |

---
## 17. Commit firmware

Commit staged firmware.

*More detail coming soon*

|Read|Write|Persists|
|---|---|---|
| `uint32` | `0 bytes` | - |

---
## 20. Incoming voltage

The incoming voltage is directly measured from the incoming 5 V line.

|Read|Write|Persists|
|---|---|---|
| `uint32` | - | - |

---
## 27. Distance output

This command configures the data output when using the [44. Distance data](command_detail?id=_44-distance-data) command. Each bit toggles the output of specific data.

|Bit|Output|
|:---:|---|
|0|First return raw|
|1|First return closest|
|2|First return median|
|3|First return furthest|
|4|First return strength|
|5|Last return raw|
|6|Last return closest|
|7|Last return median|
|8|Last return furthest|
|9|Last return strength|
|10|Background noise|

|Read|Write|Persists|
|---|---|---|
| `uint32` | `uint32` | - |

---
## 28. Communication mode

This command sets the LW20 communication start up mode.

!> Please make sure you can communicate with the LW20 on the chosen interface.

|Value|Description|
|---|---|
|0|The LW20 will start up waiting for serial or I2C interface selection. By sending a serial command the serial interface will be chosen, by sending an I2C command the I2C interface will be chosen. This is the default mode.|
|1|The serial interface is immediately chosen on start up.|
|2|The I2C interface is immediately chosen on start up.|

|Read|Write|Persists|
|---|---|---|
| `uint8` | `uint8` | Yes |

---
## 30. Stream

The LW20 can continuously output data without individual request commands being issued. Reading from the `Stream` command will indicate what type of data is being streamed. Writing to the `Stream` command will set the type of data to be streamed.

|Value|Streamed data|
|---|---|
| 0 | disabled |
| 5 | [44. Distance data](command_detail?id=_44-distance-data) |

!> Streaming commands will typically only output on the serial interface. While it is possible to read and write the Stream command over I2C, the resulting streamed data will not be retrievable.

|Read|Write|Persists|
|---|---|---|
| `uint8` | `uint8` | No |

---
## 31. Stream statistics

Reading `Statistics` will retrieve a `uint8` indicating the state of statistics streaming. Writing to `Statistics` will enable/disable streaming of [35. Statistics data](command_detail?id=_35-statistics-data) packets at 2 Hz.

|Value|Streamed data|
|---|---|
| 0 | disabled |
| 1 | enabled |

!> Streaming commands will typically only output on the serial interface. While it is possible to read and write the Statistics command over I2C, the resulting streamed data will not be retrievable.

|Read|Write|Persists|
|---|---|---|
| `uint8` | `uint8` | No |

---
## 35. Statistics data

*Serial interface only*

**8 bytes of data:**

|Offset|Type|Description|
|------|----|-----------|
|0x00 | `uint16` | Temperature in 100ths of a degree |
|0x02 | `uint16` | Bias voltage [mV] |
|0x04 | `uint16` | Bias voltage target [mV] |
|0x06 | `uint16` | Background noise |
|0x08 | `uint8` | Laser firing state |

|Read|Write|Persists|
|---|---|---|
| - | - | - |

---
## 44. Distance data

This command contains distance data as measured by the LW20. The data included will vary based on the configuration of the [27. Distance output](command_detail?id=_27-distance-output) command.

This command can be read at any time however if [30. Stream](command_detail?id=_30-stream) is set to `5` then this command will automatically output at the measurement update rate.

The data will be packed in order based on the bits set in the `Distance output` parameter.

|Data output bit|Description|Size|
|:---:|---|---|
|0|First return raw [cm]|`int16`|
|1|First return closest [cm]|`int16`|
|2|First return median [cm]|`int16`|
|3|First return furthest [cm]|`int16`|
|4|First return strength [%]|`int16`|
|5|Last return raw [cm]|`int16`|
|6|Last return closest [cm]|`int16`|
|7|Last return median [cm]|`int16`|
|8|Last return furthest [cm]|`int16`|
|9|Last return strength [%]|`int16`|
|10|Background noise|`int16`|

|Read|Write|Persists|
|---|---|---|
| - | - | - |

---
## 50. Laser firing

Reading this command will indicate the current laser firing state. Writing to this command will enable or disable the firing of the laser. 

|Value|Description|
|---|---|
|0|Disabled|
|1|Enabled|

|Read|Write|Persists|
|---|---|---|
| `uint8` | `uint8` | No |

---
## 55. Temperature

Reading this command will return the temperature in 100ths of a degree.

|Read|Write|Persists|
|---|---|---|
| `uint32` | - | - |

---
## 85. Noise

Reading this command will return the level of background noise.

|Read|Write|Persists|
|---|---|---|
| `uint32` | - | - |

---
## 88. Alarm status

Reading this command will return the status of `Alarm A` and `Alarm B`. Each alarm has a byte where `1` indicates that it has been tripped and `0` indicates a neutral state.

|Byte|Description|
|---|---|
|0|Alarm A|
|1|Alarm B|

|Read|Write|Persists|
|---|---|---|
| `2 bytes` | - | - |

---
## 90. Baud rate

The baud rate as used by the serial interface. This parameter only takes effect when the serial interface is first enabled after power-up or restart.

Reading this command will return the baud rate. Writing to this command will set the baud rate.

|Value|Baud rate [bps]|
|---|---|
|0|9600|
|1|19200|
|2|38400|
|3|57600|
|4|115200|
|5|230400|
|6|460800|
|7|921600|

|Read|Write|Persists|
|---|---|---|
| `uint8` | `uint8` | Yes |

---
## 91. I2C address

Reading this command will return the I2C address. Writing this command will set the I2C address.

!> The I2C address value is in decimal.

|Read|Write|Persists|
|---|---|---|
| `uint8` | `uint8` | Yes |

---
## 93. Measurement mode

The measurement mode controls the overall update rate of the LW20.

Reading this command will return the measurement mode. Writing this command will set the measurement mode.

|Value|Readings per second|
|---|---|
|1|48|
|2|55|
|3|64|
|4|77|
|5|97|
|6|129|
|7|194|
|8|388|

|Read|Write|Persists|
|---|---|---|
| `uint8` | `uint8` | Yes |

---
## 94. Zero offset

Zero offset in mm.

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 95. Lost signal counter

Number of lost signal measurements before lost signals are returned in the distance commands.

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 96. Alarm A distance

Alarm distance in cm.

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 97. Alarm B distance

Alarm distance in cm.

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 98. Alarm hysteresis

Alarm hysteresis distance in cm.

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 121. Servo connected

Servo connection state.

|Read|Write|Persists|
|---|---|---|
| `uint8` | `uint8` | No |

---
## 122. Servo scanning

Scanning state.

|Read|Write|Persists|
|---|---|---|
| `uint8` | `uint8` | No |

---
## 123. Servo position

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | No |

---
## 124. Servo PWM low

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 125. Servo PWM high

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 126. Servo PWM scale

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 127. Servo scan type

|Read|Write|Persists|
|---|---|---|
| `int8` | `int8` | Yes |

---
## 128. Servo scan speed

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 129. Servo lag

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 130. Servo FOV low

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 131. Servo FOV high

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 132. Servo alarm A low

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 133. Servo alarm A high

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 134. Servo alarm B low

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |

---
## 135. Servo alarm B high

|Read|Write|Persists|
|---|---|---|
| `int32` | `int32` | Yes |