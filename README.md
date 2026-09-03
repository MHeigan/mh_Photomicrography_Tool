# mh_macro_tools — Photomicrography Tool  `v2.0.0`

A precision desktop calculator for photomicrography and macro-rail
focus-stacking workflows: magnification, field of view, depth of field,
diffraction, effective aperture, resolution, and stacking steps — for both
camera-lens macro and infinity microscope-objective rigs.

© 2026 Martin P. Heigan · 
[anti-matter-3d.com](https://anti-matter-3d.com/tools/)

- - -
## Features

- **Two optical models** — camera lens (macro approximation) and infinity
  microscope objective (tube-lens scaled, NA-based).
- **Magnification** — physical and equivalent (crop-scaled); first-order
  extension term; objective tube-lens scaling against a 200 mm reference.
- **Raynox support** — DCR-150 / DCR-250 modelled as the tube/projection lens,
  with bellows placement guidance.
- **Field & sampling** — field of view (mm/µm), object pixel size, sensor
  diagonal, pixel coverage.
- **Depth of field** — camera macro model with pupil correction, and an objective
  diffraction + detector model scaled by imaging-medium refractive index.
- **Diffraction & exposure** — effective f-number, light loss in stops, Airy
  disk, and a selectable diffraction criterion (Strict / Standard / Practical)
  with neutral, criterion-relative wording and a suggested **sweet-spot aperture**
  .
- **Resolution** — Rayleigh lateral resolution, its sensor-side projection, and a
  Nyquist sampling verdict.
- **Bidirectional focus stacking** — drive the calculation by depth of field,
  step size, **or** frame count, with an effective-overlap read-out and focus-gap
  warning.
- **Live interactivity** — Auto-calculate (on by default) recomputes on every
  change; the step and frame-count fields stay editable and editing any one
  makes it the driver, so you can fiddle your way to a target.
- **Stacking modes** — Motorised Rail, Manual Focus Steps, and Single Shot.
- **Usability** — per-parameter tooltips, wavelength (UV/IR-aware) and
  pupil-magnification inputs, JSON profile load/save (backward compatible), and
  a Help → User Manual link.

## Distribution

The release ZIP contains a self-contained, signed Windows executable — no
Python or runtime install required.

```
mh_Photomicrography_Tool_v2_0_0.zip
├── mh_Photomicrography_Tool_Win_x64_v2_0_0.exe   (signed)
├── _internal\                                     (runtime — do not modify)
├── mh_Photomicrography_Tool_User_Manual.pdf
├── License_Agreement.pdf
└── README.txt
```
## System requirements


|Item            |Requirement                                |
|----------------|-------------------------------------------|
|Operating system|Windows 10 / 11 (64-bit)                   |
|Runtime         |None — Python and all libraries are bundled|
|Display         |1920 × 1080 or larger recommended          |
|Internet        |Not required to run                        |

## Files


|Type    |Format                                         |
|--------|-----------------------------------------------|
|Profiles|JSON — every input field saved/reloaded per rig|
|Results |Plain-text export of calculated outputs        |

This is a calculator; it does not open or process image or video files.

## Licence

Free for non-commercial use under **CC BY-NC-ND 4.0**, governed by the laws of
South Africa. Use and share the unmodified tool with attribution for
non-commercial purposes; no selling, no modified redistribution, no attribution
removal. No registration or licence key is required. See 
[License.md](License.md) / `License_Agreement.pdf` for full terms.

## Security

The executable is code-signed (Certum OV, RFC-3161 timestamped) and was
submitted to the Microsoft Defender (WDSI) file-submission service and then to
VirusTotal prior to release. On first launch, Windows SmartScreen may prompt
for a newly seen signed binary — choose **More info → Run anyway**.

## More tools & contact

- Tool suite — <https://anti-matter-3d.com/tools/>

