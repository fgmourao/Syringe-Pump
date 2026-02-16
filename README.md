# Open-Source Syringe Pump – Modified Version

This firmware builds upon an existing open-source syringe pump design originally developed by **Andrey Samokhin**.

The original architecture provides a robust and accessible DIY solution. This modified version introduces mechanical and firmware-level enhancements aimed at improving motion smoothness, positional control, and usability during fine experimental procedures.

### Key Priorities
* **Controlled linear displacement:** Higher precision for micro-movements.
* **Manual alignment capability:** Real-time tactile control.
* **Clear operator feedback:** Improved UI and audible alerts.

This version is particularly suitable for laboratory microinjection, syringe positioning, and preparatory alignment steps prior to automated infusion.

---

## 1. Mechanical Design Update

To improve positioning resolution and reduce stepwise linear displacement, the original lead screw was replaced with a **0.6 mm/revolution** lead screw. This modification significantly decreases the linear travel per motor step.



### Mechanical Parameters
| Parameter | Value / Detail |
| :--- | :--- |
| **Lead screw pitch** | 0.6 mm/rev |
| **Effect** | Reduced displacement per motor step; improved motion continuity |
| **Benefit** | Increased precision during microinjection and manual positioning |

---

## 2. Firmware Update – Manual Positioning Mode (Jog Control)

A dedicated **Manual Positioning Mode** has been added to the firmware, enabling direct, real-time control of the syringe position via the user interface.

### Control Mapping
* **UP button:** Forward movement (while pressed)
* **DOWN button:** Backward movement (while pressed)
* **LEFT button:** Exit positioning mode
* **RIGHT button:** Reset relative position ($mm = 0$)

### Operational Characteristics
* **Tactile Control:** Movement occurs only while a button is actively pressed.
* **Dual-Speed Operation:** * *Short press* → fine positioning.
    * *Long press* → fast positioning.
* **Efficiency:** The stepper motor driver is enabled only during active movement, reducing heat generation and electrical noise.
* **Safety:** Audible feedback (beep) when a mechanical endstop is reached.
* **Feedback:** Real-time display of relative linear displacement in millimeters.

> **Note:** This mode is intended exclusively for manual alignment and fine adjustment prior to automated infusion.

---

## 3. System Features Summary

* **High-resolution** linear positioning via fine-pitch lead screw.
* **Manual jog control** with dual-speed operation.
* **Real-time positional feedback** in millimeters.
* **Endstop detection** with audible alerts.
* **Reduced vibration** and improved motion smoothness.

---

## 4. Original Project Reference

This work is based on the original open-source syringe pump design by **Andrey Samokhin**, published on March 1, 2020.

* **Original Project Link:** [Link to Original Design](https://www.mass-spec.ru/projects/diy/syringe_pump/eng/)

*All credit for the original concept and baseline implementation belongs to the original author.*
