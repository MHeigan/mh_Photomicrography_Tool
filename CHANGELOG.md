# Changelog — mh_macro_tools Photomicrography Tool

All notable changes to this tool are documented here. Dates use ISO 8601.
Licence: CC BY-NC-ND 4.0 (non-commercial), governed by the laws of South Africa.

## [2.0.0] — 2026-06

### Changed
- Full rewrite on Python 3.13 + PySide6 (dark-amber theme), replacing the
  earlier tkinter implementation.
- Optical engine reviewed against primary references; all v1.x formulas
  confirmed accurate.

### Added
- **Diffraction / effective-aperture / exposure module**: effective f-number,
  light loss in stops, and Airy disk diameter.
- **Selectable diffraction criterion** (Strict / Standard / Practical) with
  neutral, criterion-relative wording and a suggested sweet-spot aperture.
- **Resolution / Nyquist-sampling module**: Rayleigh resolution, its sensor-side
  projection, and a sampling verdict (objective mode).
- **Bidirectional focus stacking**: drive by depth of field, step size, or frame
  count, with an effective-overlap read-out and a focus-gap warning. Live
  Auto-calculate (on by default) recomputes on every change and autofills the
  Step Size / Frame Count fields so the section stays interactive.
- **Stacking modes**: Motorised Rail, Manual Focus Steps, Single Shot, with
  gear-neutral result labels.
- Refractive-index, wavelength (UV/IR-aware), and pupil-magnification inputs;
  pupil correction applied to camera depth of field and effective aperture.
- Per-parameter tooltips and a Help → User Manual link.
- Mount-register auto-fill per camera mount.
- Wheel-safe dropdowns (scrolling the window no longer changes a hovered combo).

### Fixed
- Diffraction reporting no longer flags a normal macro lens as defective; the
  verdict is criterion-relative and reads as guidance, not an error.
- Camera mode no longer silently assumes f/4 when the F-stop field is empty:
  aperture-dependent results (DOF, effective f-number, Airy disk, diffraction
  verdict) now show dashes with an explanatory note until a lens or working
  f-stop is entered, matching objective mode's missing-NA behaviour and the
  manual's troubleshooting section. Light loss and the sweet-spot aperture,
  which depend only on magnification and pupil ratio, remain reported.
- Result displays distinguish a computed value of exactly zero from a missing
  value (is-not-None checks instead of truthiness).

### Compatibility
- Profiles from earlier versions load cleanly; new inputs default when absent.

## [1.3.4]

### Changed
- Results panel moved right for 1080p usability; refined window sizing.
- Stable Nikon CFI 200 mm + DCR-150 default profile.
- Objective f-stop disabled in objective mode.
- Raynox extension guidance aligned with tube assemblies.
