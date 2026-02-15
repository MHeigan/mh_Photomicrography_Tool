# mh_tools — Photomicrography Tool (Win x64) — v1.3.4

A precision calculator for **photomicrography** and **macro-rail focus stacking** workflows. It computes **physical magnification**, **equivalent (crop-scaled) magnification**, **field of view**, **object-space pixel size**, **depth of field (DOF)**, and **recommended rail step size / frame count** for rigs ranging from **macro lenses** to **infinity microscope objectives**.

---

## What’s included in the Windows ZIP release

Typical layout (your packaging may vary slightly):

- `mh_Photomicrography_Tool_Win_x64_v1.3.4.exe` *(Windows build; onedir)*
- `manuals/`
- `mh_Photomicrography_Tool_User_Manual_v1.3.4.pdf` *(includes the full equations appendix)*
- `README.md`
- `README.txt`
- `License_Agreement.pdf`
---

## Download the latest release at:
[http://anti-matter-3d.com/mh_tools/mh_Photomicrography_Tool_Win_x64_v1_3_4.zip](https://github.com/MHeigan/mh_Photomicrography_Tool/releases/tag/mh_Photomicrography_Tool_v1_3_4)

---

## Install & Launch (Windows) 🚀

1. **Extract** the ZIP to a normal folder (do not run from inside the ZIP).
2. Run `mh_Photomicrography_Tool_Win_x64_v1.3.4.exe`.

No installer is required.

---

## Quick Start (most common workflow)

**Default infinity-objective workflow**: **Nikon CFI-style 200 mm reference**, **PB‑6 bellows**, **Raynox DCR‑150** acting as the tube/projection lens.

1. Set **Lens Type** → **Microscope Objective (Infinity)**
2. Enter **Objective Magnification** (e.g. `10` for 10×)
3. Enter **Objective NA** (e.g. `0.25`)
4. Set **Reference Tube Focal Length** → `200 mm` *(default for Nikon CFI-type systems)*
5. Set **Raynox Lens** → `DCR‑150`
6. Set **Raynox Use Mode** → `As Tube Lens (changes magnification)`
7. Confirm **sensor parameters** (defaults are provided; tweak as needed)
8. Set **overlap** (e.g. `30%`) and **object depth/scale** (e.g. `3 mm`)
9. Click **Calculate**

---

## What the tool is modeling

### 1) Physical vs “Equivalent/Effective” magnification
- **Physical magnification** is the magnification **at the sensor** and drives FoV, pixel scale, DOF, rail step size.
- **Equivalent magnification** is a **display-only framing comparison**:

`M_equiv = M_phys × CropFactor`

Crop factor changes framing relative to full-frame; it does **not** change the physical optics at the sensor.

### 2) Infinity objectives: tube-lens scaling (core relationship)
Infinity objectives are specified for a design/reference tube lens focal length `f_ref` (commonly **200 mm** for Nikon CFI and many Mitutoyo-style systems). If the objective is labeled `M_obj` (e.g. 10×), then physical magnification is:

`M_phys = M_obj × (f_tube / f_ref)`

Where `f_tube` is the focal length of the tube/projection lens actually used.

### 3) Raynox DCR lenses in infinity-objective rigs (two roles)
Raynox close-up lenses are specified in **diopters**. A practical approximation is:

`f_raynox(mm) ≈ 1000 / D`

So:
- **DCR‑150 (~4.8D)** → `f_raynox ≈ 208.33 mm`
- **DCR‑250 (~8D)** → `f_raynox ≈ 125.00 mm`

The tool supports two real-world roles:

**A) Raynox as the tube/projection lens (modeled)**  
If you select **“As Tube Lens (changes magnification)”**, the tool uses `f_tube = f_raynox` inside the tube-lens scaling equation. This directly changes **physical magnification**.

**B) Raynox as an additional relay/quality element (not modeled as magnification)**  
If you already have a defined tube lens focal length (e.g. a real 200 mm tube lens), adding a Raynox may improve correction/quality — but any magnification change becomes spacing-dependent. The tool intentionally avoids “combining lenses” into a single unstable magnification formula in this case.

### 4) Bellows / extension guidance (focus placement helper)
When Raynox is used as the tube lens, practical assemblies often place it **roughly one focal length from the sensor**. The tool provides:
- **Raynox Required Mount Extension (mm)** *(first-order placement guideline)*
- **Raynox Extension Delta (mm)** *(your entered extension minus the guideline)*

This is a **focus/placement helper**, not a magnification equation.

---

## Macro rail & focus stacking recommendations

The tool uses DOF to recommend rail steps:

- `Step size (mm) = DOF × (1 − overlap)`
- `Recommended frames = ceil(object depth / step size)`

For objectives, DOF is modeled using a diffraction term plus a detector term (CoC factor × pixel pitch). The full derivation and equations are included in the **User Manual PDF**.

---

## Profiles (Load / Save)

- **Save Profile** writes all input fields to JSON.
- **Load Profile** restores them.

Recommended practice:
- Create named profiles per rig (example: `D500_CFI10x_PB6_DCR150.json`).
- Keep sensor parameters inside the profile so FoV/pixel scale remain consistent.

---

## Troubleshooting

- **Results show dashes**: ensure required inputs for the selected mode exist (NA for objectives; f‑stop for camera lenses).
- **Unexpected objective magnification**: verify whether Raynox is set to act as the tube lens, and confirm tube lens focal length.
- **Rail steps look extreme**: check overlap %, pixel pitch, CoC factor, and NA; objective DOF can be extremely small at higher NA.

---

## Licensing 📜

This software is licensed under: **CC BY‑NC‑ND 4.0**  
For a plain-English summary, see: `License_Agreement.pdf`

---

## Changelog (summary)

- **v1.3.4** — Results panel moved to the right for 1080p usability; refined window sizing; stable default profile for the Nikon CFI 200 mm + DCR‑150 workflow; objective f‑stop disabled in objective mode; Raynox extension guidance aligned with tube assemblies.
