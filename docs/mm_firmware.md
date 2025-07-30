The aim of this page is to provide the user with the inputs the DRV8245 motor driver requires for functionality as well as code for a typical usecase scenario that users can then modify as needed to fit their needs. This information may be applicable to people using other platforms to interface with DRV82xx series automotive grade brushed motor driver IC's. 
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
|   25  | iPROPI   | Current sense output |
|   26  | nFAULT   | Fault indication output to controller |
|   27  | MODE     | Configures control scheme based on 1 of 3 specified resistance levels |
|   28  | ITRIP    | Configuration input for high-side current limiting based on 1 of 6 specified resistance levels |


This table leaves out the main voltage input, ground, and load outputs as they are statically configured. 