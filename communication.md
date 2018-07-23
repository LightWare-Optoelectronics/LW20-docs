# Communication overview

The LW20 has two physical interfaces for communication:
- Serial UART
- I2C

Both interfaces operate over the same pair of wires on the LW20 cable. The required interface needs to be selected before any communication can occur. When the LW20 first receives power it will wait for one of the interfaces to be selected. Sending an initial command over either serial or I2C will indicate which interface to activate. See [Serial interface](serial.md) and [I2C interface](i2c.md) for more detail about each.