# Open-Source Syringe Pump – Modified Version

This firmware is a modified version of the open-source syringe pump originally developed by **Andrey Samokhin** (v0.9a, March 1, 2020).

> **Original project:** [mass-spec.ru/projects/diy/syringe_pump/eng](https://www.mass-spec.ru/projects/diy/syringe_pump/eng/)
> *All credit for the original concept and baseline implementation belongs to the original author.*

The modifications listed below were made by **Flavio Mourao** on **01/08/2026**, targeting improved motion smoothness, manual positional control, and operator safety during microinjection procedures.

---

## Change 1 — Lead screw pitch updated

The default lead screw was replaced with a **0.6 mm/revolution** unit, reducing linear displacement per motor step and resulting in smoother, more continuous motion during fine procedures.

| Parameter | Original | Modified |
| :--- | :---: | :---: |
| Lead screw pitch | 2.0 mm/rev | **0.6 mm/rev** |
| Displacement per microstep | Higher | **Reduced** |
| Motion smoothness | Standard | **Improved** |

---

## Change 2 — Manual Positioning Mode (Jog Control)

A dedicated **Positioning** entry was added to the main menu (between *Cycle Mode* and *Settings*), enabling direct real-time control of the syringe position via the existing interface buttons.

### Button mapping

| Button | Action |
| :--- | :--- |
| **UP** | Forward movement (while held) |
| **DOWN** | Backward movement (while held) |
| **LEFT** | Exit positioning mode |
| **RIGHT** | Reset relative position counter ($mm = 0$) |

### Features
* **Press-to-move:** Movement occurs only while a button is actively held.
* **Dual-speed operation:** short press → fine positioning; long press → fast positioning.
* **Power efficiency:** Stepper driver is enabled only during active movement, reducing heat and electrical noise.
* **Endstop safety:** Audible beep when a mechanical limit is reached; movement stops automatically.
* **Real-time feedback:** Relative displacement displayed in millimeters on the LCD.

> **Note:** This mode is intended for manual syringe alignment and fine adjustment prior to automated infusion.

---

## Change 3 — Startup screensaver customized

The original splash screen (*"OpenSP 0.9 / www.mass-spec.ru"*) was replaced with a custom message displayed at boot.

---

## Change 4 — Start confirmation dialog added

A `confirmStart()` function was introduced to require explicit operator confirmation before any pumping operation begins. After selecting an infusion or refill action, the LCD prompts:

```
Ready? Yes or No
< NO       YES >
```

* **RIGHT** → confirm and proceed
* **LEFT** → cancel and return to menu

This prevents accidental triggering of pumping operations.

---

## Summary

| # | Change | Scope |
| :---: | :--- | :--- |
| 1 | Lead screw pitch: 2.0 → 0.6 mm/rev | Mechanical + firmware (`MMPER360`) |
| 2 | Manual Positioning Mode (jog control) | Firmware — new function + menu entry |
| 3 | Custom startup screensaver | Firmware — `showScreensaver()` |
| 4 | Start confirmation dialog | Firmware — new `confirmStart()` + `pumpSingly()` |
