# Hybrid Lift Gearbox Workbench v3

**An interactive, browser-based concept workbench for exploring a coaxial lift gearbox that combines a nested helical planetary stage with a dual-disc cycloidal reducer.**

> **Engineering boundary:** This is an early-stage screening and visualisation tool. It does **not** certify gears, bearings, braking systems, lift safety, material selection, manufacturing tolerances, or regulatory compliance. Use it to expose assumptions, compare concepts, and identify analysis that must be validated through formal calculations, simulation, test data, and engineering review.

---

## What it does

Hybrid Lift Gearbox Workbench v3 brings kinematics, operating duty, thermal behaviour, reliability proxies, safety-interface checks, condition monitoring, and an exportable engineering diagram into one standalone HTML application.

It is designed for concept exploration of a machine-room-less lift reducer architecture featuring:

- **Stage 1 — Nested Helical Planetary (NHP):** fixed ring, sun input, carrier output.
- **Stage 2 — Cycloidal Pin Reducer:** configurable pin/lobe count, with a dual-phase disc concept for load sharing.
- **Active Backlash-Lock (ABL):** a configurable preload concept intended to reduce residual lash during reversals.
- **Integrated Micro-Pump (IMP):** a conceptual lubrication loop with oil-health and pump-health inputs.
- **Condition fusion:** combines vibration, thermal, oil, contamination, torque-slip, wear, brake margin, and sensor-confidence inputs into screening indicators.

The workbench runs entirely in a modern browser. No installation, server, account, or external dependency is required.

---

## Quick start

1. Download or clone this project.
2. Open `hybrid_lift_gearbox_workbench_v3.html` in a modern desktop browser.
3. Start with **Balanced MRL** or enter your own tooth counts, load case, duty cycle, thermal assumptions, and monitoring values.
4. Select **Run synthesis**.
5. Review the status pills, calculation report, charts, diagram overlays, and alerts.
6. Use **Find near-ratio candidates** to explore alternative tooth-count combinations.
7. Export a diagram, results summary, or complete design snapshot when needed.

### Recommended browsers

Use a current version of Chrome, Edge, Firefox, or Safari with JavaScript, SVG, Canvas, and `localStorage` enabled. SVG export is usually the most dependable output format. Some browsers may block PNG export from local files; use SVG export in that case.

---

## Main capabilities

### 1. Architecture and kinematics

- Calculates the stage ratios and combined reduction ratio.
- Calculates screened output speed, nominal torque, and peak torque.
- Supports configurable sun, ring, pin, lobe, and planetary count inputs.
- Checks basic planetary assembly phasing and simple cycloidal reduction conditions.
- Supports dual-phase cycloidal disc and herringbone-stage concept toggles.
- Searches a defined range of nearby tooth-count combinations for ratios close to a requested target.

### 2. Duty-cycle and torsional screening

- Models nominal and peak torque using duty cycle, starts per hour, acceleration/deceleration time, and a peak-torque factor.
- Includes equivalent output inertia and torsional stiffness inputs.
- Estimates a torsional natural-frequency proxy and compares it with a mesh-order proxy.
- Includes uncompensated backlash and ABL preload inputs to show residual-backlash and drag trade-offs.

### 3. Thermal, lubrication, and reliability screening

- Estimates heat loss from power flow and efficiency assumptions.
- Produces a transient housing-temperature estimate for the selected run window.
- Includes enclosure area, convection, thermal mass, oil grade, oil level, and pump-health inputs.
- Adds churning-risk and lubrication-health proxies.
- Screens basic load distribution, mesh-force, and bearing L10-life proxies using supplied face width and dynamic bearing capacity.

### 4. Safety and condition monitoring fusion

- Inputs for vibration, baseline vibration, oil health, water/contamination, measured temperature, encoder torque-slip, wear, brake-test margin, and sensor confidence.
- Backstop and soft-shear-coupling concept switches.
- Produces a condition-risk score, safety-risk score, status pills, and fault-focus hints.
- Shows monitoring contributions in a dedicated chart instead of depending on a single alarm source.

### 5. Visualisation and reporting

- Interactive engineering-style gearbox section diagram.
- Pan by dragging; zoom with a mouse wheel or trackpad; reset the view at any time.
- Toggle diagram layers independently:
  - Power and torque flow
  - Lubrication and oil-health path
  - Sensors and monitoring channels
  - Safety interface
  - Torsional/dynamic overlay
  - Housing section
  - Callouts and dimensions
- Design-balance radar chart.
- Transient-temperature chart.
- Condition-fusion chart.
- Torque-cycle proxy chart.
- Up to five saved comparison points in the browser.
- Exports for SVG, PNG, JSON design snapshots, CSV summaries, and browser print reports.

---

## Input groups

| Group | Purpose | Examples |
|---|---|---|
| Architecture & kinematics | Defines the gear concept and target ratio | Sun/ring teeth, planets, pins/lobes, module, helix angle |
| Drive & duty cycle | Sets the operating load case | Motor rpm, nominal torque, starts/hour, peak factor, output inertia |
| Torsional dynamics | Screens vibration and reversal behaviour | Stiffness, acceleration time, backlash, ABL preload |
| Thermal & lubrication | Screens heat rejection and oil conditions | Ambient, housing area, convection, thermal mass, oil grade/level, pump health |
| Reliability | Provides coarse load and life indicators | Face width, bearing dynamic rating, life target |
| Monitoring & safety | Feeds the condition-fusion and safety screens | Vibration, oil health, contamination, temperature, slip, brake margin, backstop |

All inputs are editable. Many are intentionally labelled as **proxies**, **indices**, or **screening assumptions** because they are not substitutes for fully derived physical parameters.

---

## Typical workflow

1. **Start with the ratio.** Enter a target ratio, then either define tooth counts directly or use candidate search.
2. **Set a realistic duty case.** Add speed, torque, starts per hour, acceleration/deceleration time, peak factor, and inertia.
3. **Set thermal assumptions.** Use expected ambient temperature, enclosure area, cooling conditions, housing mass, oil grade, oil level, and pump health.
4. **Review feasibility alerts.** Treat red and amber items as investigation prompts, not as automatic acceptance/rejection criteria.
5. **Explore alternatives.** Adjust planetary count, face width, ABL preload, duty, or target ratio, then save comparison points.
6. **Export the concept.** Use JSON for a machine-readable design record, CSV for summaries, SVG for drawings, and Print Report for review packs.
7. **Move to validated engineering.** Transfer the selected concept to formal gear, bearing, thermal, structural, NVH, control, safety, and lift-system analysis.

---

## Presets

The built-in presets change input values only. They are not recommended or approved product configurations.

| Preset | Intended use |
|---|---|
| **Balanced MRL** | A balanced starting point for a compact machine-room-less lift concept |
| **High-torque duty** | A heavier load / higher duty screening scenario |
| **Thermal stress** | A deliberately demanding cooling and duty scenario |
| **Condition fault** | A monitoring-focused scenario with degraded condition inputs |

---

## Exported files

| Export | Contents |
|---|---|
| `hybrid_lift_gearbox_v3.svg` | Vector drawing of the current diagram state |
| `hybrid_lift_gearbox_v3.png` | High-resolution raster image of the current diagram state |
| `hybrid_lift_gearbox_v3_design.json` | Inputs, key screening outputs, alerts, and saved comparison points |
| `hybrid_lift_gearbox_v3_summary.csv` | A compact tabular result summary |
| Print report | Browser-generated printable screen report |

---

## Data and privacy

The workbench is offline-first:

- It does not require an account or server connection.
- Current inputs and saved comparison points are stored only in the browser using `localStorage` under the key `hybrid-lift-gearbox-v3`.
- Clearing site data or browser storage removes locally saved settings and snapshots.
- Exported files are generated locally in the browser.

---

## Important limitations

The calculations are transparent **screening models**, not design certification. Do not use outputs from this workbench alone to specify, manufacture, approve, commission, or operate a lift gearbox.

The following work remains necessary for a real product programme:

- Verified involute tooth geometry, profile shift, contact ratio, root stress, pitting, micropitting, scuffing, and efficiency calculations.
- Complete cycloidal geometry, pin contact, eccentric bearing, output-pin, clearance, and manufacturing-tolerance analysis.
- Bearing selection and life calculations using real loads, duty spectrum, lubrication, contamination, internal clearance, mounting stiffness, and preload.
- Thermal-network or CFD validation using measured housing geometry, airflow, lubricant rheology, seals, churning, and real drive losses.
- Structural FEA for housing, carriers, shafts, brake interface, backstop, coupling, fasteners, and fatigue life.
- Torsional, acoustic, vibration, and control-system testing using measured motor, brake, sheave, rope, and car/load dynamics.
- Functional-safety and lift-code compliance review, including braking, overspeed, backstop behaviour, maintenance, failure modes, diagnostics, and required independent verification.

---

## File structure

```text
.
├── hybrid_lift_gearbox_workbench_v3.html  # Standalone application
└── README.md                               # Project documentation
```

The application is intentionally self-contained. Its HTML, CSS, SVG, and JavaScript are packaged in one file to make review, sharing, and offline use easy.

---

## Development notes

### Design principles

- Keep the core workbench fully local and dependency-free.
- Show assumptions and warnings rather than hiding uncertainty behind a single score.
- Prefer comparative exploration over false precision.
- Keep exports usable in engineering reviews and downstream analysis.
- Preserve a clear divide between conceptual innovation and validated mechanical design.

### Suggested next upgrades

1. Add import/export of named project files with versioned schemas.
2. Add a configurable duty-spectrum editor rather than a single duty percentage.
3. Add a proper ISO/AGMA calculation interface, with each assumption exposed and traceable.
4. Add real material libraries, lubricant viscosity-temperature curves, and bearing catalog data.
5. Add geometry export or a CAD/FEA hand-off format.
6. Add units selection with robust SI/Imperial conversion.
7. Add test-data ingestion for vibration, temperature, oil, and encoder measurements.
8. Add an auditable requirement and verification matrix for design reviews.

---

## Version history

### v3 — Advanced Workbench

- Merges the original concept diagram features with the v2 parametric workbench direction.
- Adds duty-cycle, torsional/NVH, thermal, lubrication, reliability, safety, and monitoring-fusion screens.
- Adds presets, comparison snapshots, candidate designs, CSV export, richer JSON export, and additional diagram layers.
- Maintains SVG/PNG exports, interactive diagram navigation, and browser persistence.

### Earlier versions

- **Original concept:** strong visual architecture, basic kinematics, layer toggles, pan/zoom, and diagram exports.
- **v2:** expanded parametric calculations, candidate search, thermal concepts, monitoring, and design report direction.

---

## License

No licence has been selected for this project yet. Add an explicit licence before distributing the code publicly or accepting external contributions.

---

## Contact and contribution

For engineering changes, document the following with every proposal:

- The intended use case and operating limits.
- The calculation or physical model being added.
- Assumptions, units, inputs, and expected output ranges.
- Validation evidence or a clearly marked validation plan.
- Whether the change is a visual concept, a screening proxy, or a validated design method.

This keeps the workbench useful, innovative, and honest about what has—and has not—been proven.
