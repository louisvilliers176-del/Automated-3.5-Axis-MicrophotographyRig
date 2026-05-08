# Automated 3.5-Axis Microphotography Rig

![3D Render](./Images/3DRender.png)

## Overview
This project is a high-precision, automated 3.5-axis CNC system designed specifically for extreme macro photography and focus stacking. 

Unlike standard macro rails, this rig features three spatial positioning axes (X, Y, Z) and a unique **4th "M" axis (Magnification)**. This M-axis physically controls the optical tube extension (bellows), allowing you to dial in the exact optimal focus point and magnification ratio. The custom software suite perfectly synchronizes hardware movements and camera triggering, completely automating the tedious focus-stacking acquisition process.

## Camera & Optics Setup

![Real Life Setup](./Images/image_2026-05-08_202343856.png)

The system is highly adaptable. My personal setup shown above features:
* **Camera:** Panasonic Lumix G7
* **Objective:** Nikon M-plan 10x 210/0- 0.25
* **Extension:** Standard macro bellows

**Modularity & Customization:**
Because every photographer has different gear, the adapters securing the camera, the bellows, and the objective to the aluminum plates are meant to be **3D printed** according to your specific equipment. 
*If you use infinity-corrected objectives*, the design easily accommodates a 3D-printed housing to integrate a tube lens (like a Raynox DCR-150 or DCR-250) directly into the optical path.

## Software Suite & Workflow

The hardware is driven by a comprehensive, modular software ecosystem designed to separate the acquisition station from your post-processing workstation.

### The Tools
1. **CMCS (CNC Microphotography Control Software):** The main interface. It drives the CNC, automates the focus-stacking sequence, manages X-axis optical compensation during M-axis moves, and logs all session data to a CSV file.
2. **DustMap & PoissonProfiler (Optional):** Calibration utilities to create flat-field correction maps (sensor dust/vignetting) and model sensor noise (Anscombe denoising) to be applied automatically by PostWatcher.
3. **PostWatcher:** A data management tool. Once you plug your SD card into your editing PC, it automatically sorts, renames, and transfers the RAW images to your working directory, organizing them into subfolders per stack.


### Workflow
1. **Acquire:** Use CMCS on a laptop connected to the rig to position the subject, set your bounds, and let the CNC shoot the hundreds of required frames automatically.
2. **Transfer:** Open PostWatcher on your powerful main PC to automatically ingest and organize the raw files from your SD card.
3. **Process:** (Optional) Apply DustMap and Noise reduction during transfer with PostWatcher, then import the perfectly organized stacks into your focus stacking software (Helicon Focus, Zerene Stacker).

*[Read the full Software Technical Documentation here](./Software_Documentation/Technical_Documentation_-_CNC_Microphotography_Control_Software.pdf)*

*(Note: Ready-to-use Windows `.exe` files for all software tools are available in the **Releases** section!)*

---

## BOM: Custom Parts

These parts must be manufactured according to the detailed blueprints in the `/Mechanical_Drawings` folder.

| ID | Name | Qty | Material | Ref. Plan |
| :--- | :--- | :--- | :--- | :--- |
| **X-01** | X-Axis Motor Mount Plate | 1 | Aluminum 10mm | [Page 1](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |
| **X-02** | X-Axis End Plate | 1 | Aluminum 10mm | [Page 2](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |
| **X-03** | X-Axis Carriage Plate | 1 | Aluminum 15mm | [Page 3](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |
| **SP-01** | SCS8UU Spacer | 8 | Aluminum 10mm | [Page 4](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |
| **SP-02** | T8 Nut Spacer | 2 | Aluminum 10mm | [Page 4](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |
| **M-01** | M-axis Motor Mount Plate | 1 | Aluminum 10mm | [Page 5](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |
| **M-02** | M-Axis Carriage Plate | 1 | Aluminum 12mm | [Page 7](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |
| **M-03** | M-axis End Plate | 1 | Aluminum 10mm | [Page 6](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |
| **Y-01** | Y-Axis Motor Mount Plate | 1 | Aluminum 10mm | [Page 9](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |
| **Y-02** | Y-Axis End Plate | 1 | Aluminum 10mm | [Page 10](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |
| **Z-01** | Z-Axis Carriage Plate | 1 | Aluminum 10mm | [Page 8](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |
| **Z-02** | Z-Axis End Plate | 1 | Aluminum 10mm | [Page 11](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |
| **Z-03** | Z-Axis Carrier | 1 | Aluminum 15mm | [Page 12](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |
| **Z-04** | Specimen holder | 1 | Aluminum 20mm | [Page 13](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |
| **Z-05** | Vertical Lead Screw Spacer | 2 | Aluminum 10mm | [Page 13](./Mechanical_Drawings/Microphotography_Rig_Plans_V1.pdf) |

---

## BOM: Standard Hardware

### Mechanical Components (Structure & Movement)
| Category | Component | Specification | Qty |
| :--- | :--- | :--- | :--- |
| **Motors** | Nema 17 Stepper Motor | 50mm body (High torque) | 4 |
| **Frame** | 2020 V-Slot Extrusion | 350mm / 250mm / 150mm | 2 / 2 / 2 |
| **Linear Rods** | Hardened Steel Rods | 8mm (250mm / 200mm / 150mm) | 4 / 2 / 2 |
| **Linear Rails** | MGN7C Linear Rail | 150mm + Carriage | 2 |
| **Lead Screws** | T8 Lead Screw | Lead 2mm (350/250/200/150mm) | 1 / 1 / 1 / 1 |
| **Bearings** | SCS8UU / LM8UU | Linear bearings | 8 / 2 |
| **Transmission** | T8 Brass Nut / Nut Seat | - | 4 / 2 |
| **Transmission** | Rigid Coupler | 5mm to 8mm | 4 |
| **Bearings** | 608ZZ Bearing | 8x22x7mm | 4 |

### Fasteners
| Type | Specification | Qty | Application |
| :--- | :--- | :--- | :--- |
| **M5 Screw** | M5x20mm | 22 | Frame assembly (T-Nuts required) |
| **M4 Screw** | M4x30mm | 48 | Main plates & Carriage assembly |
| **M4 Screw** | M4x10mm | 4 | Fixation Specimen holder & Lead screw spacer to MGN7C |
| **M3 Screw** | M3x12mm | 28 | Motors & small parts |
| **M2 Screw** | M2x20mm | 4 | Linear rails to 2020 Profiles (drilled/tapped) |
| **M2 Screw** | M2x14mm | 4 | Z-axis specific assembly |
| **Grub Screw** | Headless M4x4mm | 16 | Locking components |

### Electronics
| Component | Specification | Qty |
| :--- | :--- | :--- |
| **Control Board** | Makerbase TinyBee | ESP32-based CNC Board | 1 |
| **Stepper Drivers** | TMC2209 | Silent StepStick (Highly recommended) | 4 |
| **Power Supply** | 24V PSU | Recommended 10A+ | 1 |

### Electronics
| Component | Specification | Qty |
| :--- | :--- | :--- |
| **Control Board** | Makerbase TinyBee | ESP32-based CNC Board | 1 |
| **Stepper Drivers** | TMC2209 | Silent StepStick (Highly recommended) | 4 |
| **Power Supply** | 24V PSU | Recommended 10A+ | 1 |

---
## Future Roadmap

This project is an evolving platform, with several major hardware and software upgrades currently in active development:

### Advanced Lighting & Optics
* **Cold Light / Fiber Optics:** I am developing a high-intensity fiber optic system to provide "cold" illumination, preventing thermal damage to delicate biological specimens during long acquisition sequences.
* **Cross-Polarization:** Integration of polarized filters to eliminate specular reflections and achieve perfect light diffusion on shiny or metallic subjects.
* **Fluorescence Imaging:** Future support for single-wavelength light sources to enable automated fluorescence micro-photography.

### Custom Stacking Engine
* While generic stacking software is effective, I am working on a **bespoke stacking engine** tailored specifically for this rig.
* By leveraging the **exact XYZ coordinates** recorded by the CNC for every single frame, this software aims to surpass generic tools in registration accuracy and depth blending, utilizing the machine's sub-micron precision to its full potential.

---
## Gallery
*Here are some microphotography results achieved using this rig:*

### Acanthomyrmex thailandensis :
- Total Photos: 1,452
- Stack Configuration: 12 tiles (stacks), 121 photos per stack
- Imaged Area: 3806 x 3640 x 1404 µm
- Resolution: 9779 x 6519 px
- Total Capture Time: 51 minutes and 33 seconds
- Objective: Nikon M-Plan 10x 210/0, 0.25 NA
- Magnification: 10:1
- Lateral Overlap: 40%
- Focus Overlap: 20%
![Acanthomyrmex thailandensis](./Images/Gallery/Acanthomyrmex-thailandensis.jpg)

### Pseudoneoponera rufipes :
- Total Photos: 3,460
- Stack Configuration: 20 tiles (stacks), 173 photos per stack
- Imaged Area: 5882 x 3640 x 2000,6 µm
- Resolution: 9779 x 6519 px
- Total Capture Time: 2 hours 19 minutes and 40 seconds
- Objective: Nikon M-Plan 10x 210/0, 0.25 NA
- Magnification: 10:1
- Lateral Overlap: 40%
- Focus Overlap: 20%
![Pseudoneoponera rufipes](./Images/Gallery/Pseudoneoponera-rufipes.jpg)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
