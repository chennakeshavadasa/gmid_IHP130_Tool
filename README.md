# IHP SG13G2 gm/ID Explorer

**Author: Nithin Purushothama**

An interactive web tool for gm/ID-based MOSFET design using IHP's SG13G2 130nm BiCMOS open-source PDK.

**Live tool:** [https://chennakeshavadasa.github.io/gmid_IHP130_Tool/](https://chennakeshavadasa.github.io/gmid_IHP130_Tool/)

---

## Features

### gm/ID Explorer
- 7 plot types: `gm/ID vs Vgs`, `gm/ID vs Vov`, `gm/gds vs gm/ID`, `ID/W vs gm/ID`, `fT vs gm/ID`, `Cgd/Cgg`, `Cgs/Cgg`
- Overview mode: 6 mini-plots in a grid
- 4 devices: LV-NMOS, LV-PMOS, HV-NMOS, HV-PMOS
- 13 channel lengths (0.13µm – 3.0µm for LV; 0.5µm – 3.0µm for HV)
- Interactive vertical crosshair with interpolated hover values
- Log X / Log Y toggles, PNG export

### Design Helper
- σ-normalised weighted L² optimiser
- Matches the gm/ID design methodology from the `gmid_IHP130` notebook
- Inputs: target gm/ID, target gm/gds, hard gm/gds lower bound, weights w₁/w₂
- Outputs: scatter plot, loss surface, convergence trace, top-5 matching operating points

### PDK Reference
- Device specs (Vth, Lmin, Idsat, fT) sourced from IHP official documentation
- Passive components: rsil, rppd, rhigh resistors, MIM/MOM capacitors, inductors
- 7-layer Al metal stack details
- Process corners and simulation setup
- EDA tools and links to all official resources

---

## Data Source

Characterisation data from: [gmid_IHP130](https://github.com/chennakeshavadasa/gmid_IHP130)

- Simulator: **ngspice ≥ 38** (PSP 103 compact model)
- Corner: **TT (typical-typical)**
- Temperature: **27°C (300 K)**
- Bias: **V_DS = V_DD/2**, **V_SB = 0**, **W = 2 µm**
- Sweep: V_GS from 0.01V to V_DD (16401 pts LV, 32901 pts HV)
- Web delivery: 300 points/curve (downsampled)

---

## Deployment

This is a **single-file self-contained web app** — no server, no build step, no dependencies to install.

### GitHub Pages (recommended)

1. Fork or clone this repo
2. Go to **Settings → Pages**
3. Source: **Deploy from a branch** → `main` → `/ (root)`
4. Save — live at `https://your-username.github.io/your-repo-name` in ~60 seconds

### Local preview

```bash
# Any of these work:
python3 -m http.server 8080
npx serve .
open index.html   # macOS (direct file open also works)
```

---

## Technology

| Component | Details |
|-----------|---------|
| Plotly.js 2.27 | Interactive charts (CDN) |
| JetBrains Mono | Monospace font (Google Fonts CDN) |
| Pure HTML/CSS/JS | Zero build toolchain |
| Data format | JSON (embedded, 839 KB) |

---

## References

| Resource | Link |
|----------|------|
| IHP-Open-PDK GitHub | https://github.com/IHP-GmbH/IHP-Open-PDK |
| Official PDK Docs | https://ihp-open-pdk-docs.readthedocs.io |
| gmid_IHP130 data | https://github.com/chennakeshavadasa/gmid_IHP130 |
| JKU Analog Design Course | https://iic-jku.github.io/analog-circuit-design/ |

---

## License

Tool code: MIT License — free to use, modify, and distribute.  
PDK data and models: Apache 2.0 (Copyright 2024 IHP PDK Authors).

---
