# Firmware

<img src="/assets/images/mm/logo.png" class="page-logo" alt="Mighty Mouse Logo">

This page aims to document the functions of the Mighty Mouse firmware as well as the requirements of the DRV8245 motor driver for proper function, enabling users to build on or modify the code as desired. Since the Mighty Mouse firmware is still in development and some of these features / options are not yet implemented, I will simply document what I can and update this page as the firmware is further developed. 

---

To start, we should understand the I/O of the chip we're working with. The DRV8245 is designed for automotive and industrial applications and as such has more features and associated I/O than the typical motor drivers used in R/C ESC's. The Mighty Mouse project uses the HW variant of the driver in the HTSSOP package and its pinout is as follows:

| Pin # | Pin Name | Function | 
|-------|----------|----------|
|   1   |    SR    | Adjusts Slew Rate of output based on 1 of 6 specified resistance levels|
|   2   | DIAG     | Configure LATCH/RETRY settings for fault detection |
|   3   | PH/IN2   | Control direction of motor output in PH/EN mode with HIGH/LOW state |
|   4   | EN/IN1   | Control speed of motor output in PH/EN mode with PWM Duty Cycle |
|   5   | DRVOFF   | Disable motor output based on HIGH/LOW state |
|   24  | nSLEEP   | Place the driver in low-power sleep mode based on HIGH/LOW state |
|   25  | IPROPI   | Current sense output |
|   26  | nFAULT   | Fault indication output to controller |
|   27  | MODE     | Configures control scheme based on 1 of 3 specified resistance levels |
|   28  | ITRIP    | Configuration input for high-side current limiting based on 1 of 6 specified resistance levels |


This table leaves out the main voltage input, ground, and load outputs as they are not pertinent to the coding of the device. Also, a number of the I/O listed above are configured with a LVL1of6 or LVL1of3 (as Texas Instruments would call it) hardware configuration, essentially configuring the setting with a resistance level corresponding to the desired level as listed in the datasheet for the motor driver. The DIAG, MODE, and SR pins are statically conffigured as LVL1, e.g. tied to ground. At this time the settings for ITRIP and IPROPI are still being determined via testing with the development boards. 