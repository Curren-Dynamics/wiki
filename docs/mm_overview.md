<img src="/assets/images/mm/logo.png" class="page-logo" alt="Mighty Mouse Logo">

The Mighty Mouse project aims to provide a small, programmable and affordable ESC shield for the Arduino Pro Micro platform.

---

<img src="/assets/images/mm_pm_front_white.png" class="render-smooth" alt="3D Render of Mighty Mouse Pro Micro">

## Primary goals for the board:

- Roughly the same size and shape as Arduino Pro Micro
- XT30 connector for battery input
- Voltage regulation circuit to feed the Pro Micro and radio reciever
- Three pin header with standard servo |+|-|S| configuration
- DRV8245 motor driver with solder pads to connect to a brushed motor 

## Secondary goals for the board:

- DRV8245 should be able to provide the Pro Micro with current sensing
- The servo signal should support being programmed as an F.Port channel for serial communication with the radio reciever enabling multiple channel inputs and telemetry feedback from the Arduino 
- Package size of 37mm x 18mm 

---

### Current Progress

This project is currently in the prototyping and testing stage. The development boards have been assembled and are undergoing testing in various configurations to determine the exact trace routing and hardware configurations that need to be implemented in the production version of the Mighty Mouse. The board has been tested up to 28V and has produced impressive results for it's tiny size, powering motors as large as a 21T 550 Motor (Traxxas Titan) without overheating! Early versions of the Mighty Mouse firmware are being developed on this board alongside the hardware testing, you can read more on the [firmware page](mm_firmware.md)!

---
<div align="center">
Mighty Mouse Dev Board V1.0.2
</div>

<img src="/assets/images/mm/mm_dev_v102_front_white.png" class="render-smooth" alt="3D Render of Mighty Mouse Dev 1.0.2>