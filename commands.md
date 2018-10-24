# Command list

!> If a command is not readable or writable then it can only be received from the LW20 and not sent to it.

|ID|Name|Description|RW|Read bytes|Write bytes|Persists|
|---|---|---|---|---|---|---|
|0	|[Product name](command_detail?id=_0-product-name)		        	|Product name									|R	|16	|-	|-|
|1	|[Hardware version](command_detail?id=_1-hardware-version)	    	|Hardware revision								|R	|4	|-	|-|
|2	|[Firmware version](command_detail?id=_2-firmware-version)	    	|Firmware revision								|R	|4	|-	|-|
|3	|[Serial number](command_detail?id=_3-serial-number)		    	|Serial number									|R	|16	|-	|-|
|7	|[UTF8 text message](command_detail?id=_7-utf8-text-message)		|Human readable text message					|-	|-	|-	|-|
|9	|[User data](command_detail?id=_9-user-data)				        |16 byte store for user data					|RW	|16	|16	|Y|
|10	|[Token](command_detail?id=_10-token)					            |Next usable safety token      				    |R	|2	|-	|-|
|12	|[Save parameters](command_detail?id=_12-save-parameters)		    |Store persistable parameters					|W	|-	|2	|-|
|14	|[Reset](command_detail?id=_14-reset)       		                |Restart the unit            					|W	|-	|2	|-|
|16	|[Stage firmware](command_detail?id=_16-stage-firmware)			    |Upload firmware file pages 					|RW	|4	|130 |-|
|17	|[Commit firmware](command_detail?id=_17-commit-firmware)			|Apply staged firmware         					|RW	|4	|0	|-|
|20	|[Incoming voltage](command_detail?id=_20-incoming-voltage)		    |Measured incoming voltage                      |R	|4	|-	|-|
|27	|[Distance output](command_detail?id=_27-distance-output)           |Distance output configuration                  |RW	|4	|4	|Y|
|28	|[Communication mode](command_detail?id=_28-communication-mode)		|Communication start up mode 					|RW	|1	|1	|Y|
|30	|[Stream](command_detail?id=_30-stream)				                |Current data stream type						|RW	|4	|4	|N|
|31	|[Stream statistics](command_detail?id=_31-statistics)	    	    |Enable/disable statistics streaming			|RW	|1	|1	|N|
|35	|[Statistics data](command_detail?id=_35-statistics-data)		    |General status information						|-	|-	|-	|-|
|43	|[Signal probability data](command_detail?id=_43-signal-probability-data) |Signal probability data          						|-	|-	|-	|-|
|40	|[Raw distance data](command_detail?id=_40-raw-distance-data)       |Raw measurment distance data					|R	|*varies*|-	|-|
|44	|[Distance data](command_detail?id=_44-distance-data)		        |Measurment distance data						|R	|*varies*|-	|-|
|50	|[Laser firing](command_detail?id=_50-laser-firing)		     		|Is laser firing?								|RW	|1	|1	|N|
|55	|[Temperature](command_detail?id=_55-temperature)		     	  	|Measured temperature							|R	|4	|-	|-|
|70	|[High speed mode](command_detail?id=_70-high-speed-mode)		    |Toggle 20 kHz mode          					|RW	|1	|1	|Y|
|85	|[Noise](command_detail?id=_85-noise)		                		|Measured background noise						|R	|4	|-	|-|
|88	|[Alarm status](command_detail?id=_88-alarm-status)		        	|Status of alarm A & B 							|R	|2	|-	|-|
|90	|[Baud rate](command_detail?id=_90-baud-rate)		            	|Serial baud rate								|RW	|1	|1	|Y|
|91	|[I2C address](command_detail?id=_91-i2c-address)		        	|I2C address									|RW	|1	|1	|Y|
|93	|[Measurement mode](command_detail?id=_93-measurement-mode)		    |Update rate mode								|RW	|1	|1	|Y|
|94	|[Zero offset](command_detail?id=_94-zero-offset)		        	|Distance offset in MM							|RW	|4	|4	|Y|
|95	|[Lost signal counter](command_detail?id=_95-lost-signal-counter)	|Number of lost signals							|RW	|4	|4	|Y|
|96	|[Alarm A distance](command_detail?id=_96-alarm-a-distance)		    |Alarm A distance trigger						|RW	|4	|4	|Y|
|97	|[Alarm B distance](command_detail?id=_97-alarm-b-distance)		    |Alarm B distance trigger						|RW	|4	|4	|Y|
|98	|[Alarm hysteresis](command_detail?id=_98-alarm-hysteresis)		    |Alarm A & B hysteresis distance				|RW	|4	|4	|Y|
|121|[Servo connected](command_detail?id=_121-servo-connected)		    |Connect/disconnect servo						|RW	|1	|1	|N|
|122|[Servo scanning](command_detail?id=_122-servo-scanning)		    |Start/stop scan								|RW	|1	|1	|N|
|123|[Servo position](command_detail?id=_123-servo-position)		    |Servo position									|RW	|4	|4	|N|
|124|[Servo PWM low](command_detail?id=_124-servo-pwm-low)		        |Servo minimum PWM number						|RW	|4	|4	|Y|
|125|[Servo PWM high](command_detail?id=_125-servo-pwm-high)		    |Servo maximum PWM number						|RW	|4	|4	|Y|
|126|[Servo PWM scale](command_detail?id=_126-servo-pwm-scale)		    |Microseconds per degree						|RW	|4	|4	|Y|
|127|[Servo scan type](command_detail?id=_127-servo-scan-type)		    |Unidirectional/Bidirectional					|RW	|1	|1	|Y|
|128|[Servo scan speed](command_detail?id=_128-servo-scan-speed)		|Steps per reading								|RW	|4	|4	|Y|
|129|[Servo lag](command_detail?id=_129-servo-lag)		            	|Servo lag										|RW	|4	|4	|Y|
|130|[Servo FOV low](command_detail?id=_130-servo-fov-low)		        |Field of view low angle						|RW	|4	|4	|Y|
|131|[Servo FOV high](command_detail?id=_131-servo-fov-high)		    |Field of view high angle						|RW	|4	|4	|Y|
|132|[Servo alarm A low](command_detail?id=_132-servo-alarm-a-low)		|Alarm A low angle								|RW	|4	|4	|Y|
|133|[Servo alarm A high](command_detail?id=_133-servo-alarm-a-high)	|Alarm A high angle								|RW	|4	|4	|Y|
|134|[Servo alarm B low](command_detail?id=_134-servo-alarm-b-low)		|Alarm B low angle								|RW	|4	|4	|Y|
|135|[Servo alarm B high](command_detail?id=_135-servo-alarm-b-high)	|Alarm B high angle								|RW	|4	|4	|Y|