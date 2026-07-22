# Famous Curves — JSFX Plugin Suite

**A JSFX plugin suite for generating famous curves as spatial trajectories, built for music composition and electroacoustic music production in REAPER.**
Latest Release: [![GitHub release](https://img.shields.io/github/v/release/ink-sol/FamousCurves-Suite)](https://github.com/ink-sol/FamousCurves-Suite/releases)

Developed as part of the research project *"Diseño y desarrollo de software orientado a la generación de curvas notables para su uso en la producción y enseñanza de música electroacústica"*, carried out at the Escuela de Música, Facultad de Humanidades y Artes, Universidad Nacional de Rosario (UNR), under the CIN's *Becas Estímulo a las Vocaciones Científicas 2024* program.

---

## Overview

Famous Curves is a set of real-time curve generators written in **JSFX**, designed to be dropped directly into REAPER. Each plugin computes, by blocks of samples, the X/Y coordinates of a point moving along a well-known mathematical curve (circles, Lissajous figures, spirographs, polar roses, spirals, and more), normalized to the **[-1, 1]** range on both axes.

These coordinates can be used to:
- Drive the position of a virtual sound source in a **spatializer/panner** plugin.
- Modulate any other synthesis or mixing parameter over time, following the shape of the curve.
- Be recorded as **automation** for reproducible, non-real-time use.

Each plugin includes a built-in **real-time graphical display** so you can preview the trajectory before (and while) linking it to other parameters.

## Features

- Real-time curve generation and visualization inside the plugin UI.
- Common parameter set shared across the whole suite (Frequency, Amplitude, Phase Offset, Rotation, Alpha/trail persistence).
- Per-curve dedicated parameters for fine control of each curve family.
- Transport controls (Play A / Play B / Pause / Stop) for retriggering and automatable state.
- Two boundary behaviors: **Wrap** (re-enters from the opposite edge) and **Limit** (clamps to the plane).
- Direction toggle for the curve's generation sense.
- Mouse interaction on the display: Shift+Drag to move the curve's center (X/Y offset), mouse wheel to zoom/scale amplitude.
- Presets for notable special cases of each curve family.

## The Curves

| Plugin | Description |
|---|---|
| **Circumference / Ellipse** | Uniform circular motion around a fixed center; ellipses via independent X/Y amplitude ratio. |
| **Lissajous** | Two independent sinusoidal motions in X and Y; frequency/amplitude ratio and phase offset shape lines, circles, figure-eights, and more complex trajectories. |
| **Spirograph** | Hypotrochoid/epitrochoid curves from a point on a rolling circle (radius `r`) around a fixed circle (radius `R`), at distance `d` from the rolling circle's center — includes special cases like deltoid, astroid, cardioid, nephroid, and Limaçon of Pascal. |
| **Rhodonea** | Polar rose curves, where the number of petals is controlled by the parameter `k` (integer or rational). |
| **Spirals** | A family of polar spirals (Archimedean, Hyperbolic, Logarithmic, Lituus, Fermat, Cochleoid, Poinsot secant/cosecant, Epispiral, Sinusoidal spiral +/-), each with its own `Shape` and `Turns` behavior. |

## Requirements

- [REAPER](https://www.reaper.fm/) 
- A spatializer/panner plugin capable of parameter modulation or MIDI/FX parameter linking (e.g. REAPER's built-in JS spatializers or any third-party panner).

## Installation

1. Copy the `.jsfx` files into your REAPER `Effects` folder (or a custom subfolder under it).
2. Reload REAPER's FX list (Actions → "FX: Rescan all effects" or restart REAPER).
3. The plugins will appear under the **Famous Curves** category in the FX browser.

## Basic Usage

1. Insert a Famous Curves plugin and a spatializer on the same track/item.
2. Link the spatializer's position parameters to the generator's **X (Readout)** and **Y (Readout)** outputs:
   - Move the target parameter on the spatializer.
   - Open **Param → Parameter Modulation/MIDI Link**.
   - Confirm the parameter shows as *Last Touched*.
   - Enable **Link from MIDI or FX Parameter**, click `(none)`, and select the corresponding Famous Curves plugin.
   - Choose the **X (Readout)** parameter, then adjust **Offset**/**Scale** so the source's movement matches the curve preview.
   - Repeat for **Y (Readout)**.
3. Adjust the curve's parameters (or pick a preset) and confirm the trajectory in the spatializer matches the plugin's display. Curve parameters other than the X/Y outputs can also be automated.
4. Arm and record automation on the spatializer.
5. Play back the automation.

### Transport states

- **Play A / Play B** — two independent play states, each resetting the curve to its Phase Offset on trigger; alternating between them enables retriggering.
- **Pause** — freezes generation at the last computed point; resumable from Play A/B.
- **Stop** — resets and halts generation; useful for setting the initial position.

### Recording automation tips

- Set initial curve conditions (frequency, amplitude, phase offset, rotation, etc.) **before** arming envelopes — once an envelope is active, that parameter can no longer be edited from the plugin UI directly (it reads from the envelope instead).
- Use **Touch** automation mode with Shift+Click on the display to set instantaneous X/Y offsets at a specific point in time.
- Set the track's automation mode to **Write**, arm the desired parameters, and play the project to capture the resulting envelopes.

## Project Background

This suite was developed as part of an undergraduate research fellowship (CIN — *Becas Estímulo a las Vocaciones Científicas 2024*) at the Escuela de Música, Facultad de Humanidades y Artes, Universidad Nacional de Rosario, Argentina. Its goal is to provide composers and electroacoustic music students with an accessible, visual tool for generating spatial trajectories based on famous mathematical curves.

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

## Credits

Developed by Iñaki Solá during 2025-2026 at the Escuela de Música, Facultad de Humanidades y Artes, Universidad Nacional de Rosario (UNR), Argentina.
