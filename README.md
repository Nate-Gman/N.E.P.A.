# N.E.P.A. — Network-based Environmental Perception & Analysis

**A single-file Python research platform that treats the entire radio-frequency spectrum as a
sense of sight** — fusing every available wireless instrument (WiFi CSI, SDRs, passive radar,
mmWave, EEG/BCI, public satellite & astronomy data) into one navigable, persistent 3D digital
mirror of the sensed world, with an AI overseer for humanitarian threat awareness.

> **Prime directive: NO FALSE DATA, EVER.** Every value shown is either really measured, or
> explicitly flagged as inferred / estimated / simulated / proxy / penetration-limited /
> synthesized. The program is engineered to refuse to fabricate — where physics forbids something
> (seeing through metal, decoding the literal content of thoughts, omniscient global sight from one
> laptop), it reports the barrier honestly instead of faking a result.

- **Single file:** `N.E.P.A.py` (~253,000+ lines, one monolithic, copy-paste-runnable script)
- **Capability chain:** V1 → V63 (~151 additive subsystems) + v300++++ physics/relativistic/WGS-84 upgrades + **v301 Simulation.py integration (wizard tower, kinetic prediction, atomic reality render)**
- **Self-verification:** 147 built-in self-tests (`--self-test`), re-run live every 120 s + 195-function zero-error verification suite + v301 integration suite (`_v301_test.py`)
- **Physics fidelity:** exact SI constants, full WGS-84 ellipsoid geodesy (Vincenty), full special-relativity Doppler, disciplined time (GNSS > NTP > wall clock), **Velocity Verlet kinetic rewind/predict**
- **Embedded simulation:** the complete Simulation.py (72,646 lines) is embedded verbatim inside `N.E.P.A.py` under `if _NEPA_SIM_RENDER_MODE:` — default OFF, launched on **F5** hotkey
- **License/use:** research, educational, and defensive/humanitarian use only

---

## Table of Contents
1. [What this program is](#1-what-this-program-is)
2. [The goal (the grand vision)](#2-the-goal-the-grand-vision)
3. [What it can actually do today](#3-what-it-can-actually-do-today)
4. [How close is it? — the honest scorecard](#4-how-close-is-it--the-honest-scorecard)
5. [Global / galactic / universal scale — the truth](#5-global--galactic--universal-scale--the-truth)
6. [Architecture & the V1→V63 capability stack](#6-architecture--the-v1v63-capability-stack)
7. [The honesty model (provenance tiers)](#7-the-honesty-model-provenance-tiers)
8. [Installing & running](#8-installing--running)
9. [The interface — tabs, keys, and views](#9-the-interface--tabs-keys-and-views)
10. [Command-line flags](#10-command-line-flags)
11. [Getting more out of it (better data → better sight)](#11-getting-more-out-of-it-better-data--better-sight)
12. [Ethics, privacy & safety](#12-ethics-privacy--safety)
13. [FAQ](#13-faq)

---

## 1. What this program is

N.E.P.A. is a **wireless-sensing and reconstruction platform**. Ordinary radios (your WiFi router,
a phone, an SDR dongle) constantly bounce signals off everything around them — walls, furniture,
people, even the rise and fall of a chest as someone breathes. Those reflections, phase shifts, and
Doppler effects carry information about the physical world. N.E.P.A. captures that information from
**any instrument it can reach**, correlates it across frequency bands, time, and space, and
reconstructs it into a **navigable 3D scene you can fly through** — a "digital mirror" built from
radio instead of light.

It is the spiritual analogue of how a brain works: your eyes don't *see* the world, they receive
photons and your brain *constructs* a model. N.E.P.A. receives RF measurements and constructs a
model — then renders that model so a human (or its AI overseer) can navigate and understand it.

**It is a research/simulation platform, not a deployed surveillance system.** On a normal laptop
with only WiFi, it runs largely in honest simulation + local-sensing mode. As you attach real
hardware (a second receiver, an SDR, EEG, GPS), more of it "flips to live" automatically.

---

## 2. The goal (the grand vision)

The full ambition, as written in the project's own vision documents (`plan2.md`):

> Use multi-instrument spectrum-as-vision sensing to **globally paint a navigable real-time 3D copy
> of the world.** Correlate all receptions across massive matrices with heavy error correction and
> provenance. Maximize penetration and visibility using total-spectrum correlation overlay to "see
> almost everything possible." Implement strong wireless BCI that creates **persistent, savable,
> animatable digital resonance twins** of people and life forms. Enable **real-time global scanning,
> recording, forensic replay, and an AI overseer for humanitarian threat, victimization, and crime
> detection** — a protective, life-saving planetary nervous system.

The deeper purpose is **humanitarian**: turn the invisible electromagnetic world into visible,
actionable understanding to protect life, reduce suffering, and increase safety.

That is the north star. The rest of this README is about **how much of it is real, how much is an
honest simulation-first scaffold, and how much is physically gated** — because telling you the truth
about that is the whole point of the project.

---

## 3. What it can actually do today

These are **really implemented and self-verified** (each has a `.verify()` benchmark counted in the
147-check `--self-test`):

### Sensing & signal processing (real DSP on real or simulated signals)
- **WiFi CSI capture** (Nexmon / ESP32 / pcap passive sniffing) and **passive radar** (CAF + CFAR,
  ECA/Wiener-MRE, MUSIC direction-of-arrival 360°, omega-k / MIMO-SAR 3D imaging).
- **Multi-band spectrum sensing** (2.4 GHz → 300 GHz), SDR IQ, cyclostationary detection, energy
  detection, emitter fingerprinting & a co-occurrence identity graph.
- **Super-resolution** beyond the raw FFT cell: synthetic bandwidth, aperture synthesis (SAR),
  compressed sensing, coherent integration, CLEAN deconvolution, multi-frame super-resolution.
- **Penetration modeling** with *real* electromagnetic skin-depth physics per material — drywall and
  wood: yes; **metal and thick concrete: reported as blocked, never faked.**

### Reconstruction & rendering
- **Navigable 3D world** with a free-fly WASD camera, Gaussian splatting, volumetric ray-marching
  ("see-inside" x-ray metaphor), surface meshing, and dense-field interpolation — every point
  carries a confidence value and a provenance tag.
- **Spectrum-as-light**: band energy → luminance, frequency → hue (honest false-color), plus
  **spectrum sonification** (hear the spectrum; flagged as derived audio).
- **Export** of the reconstructed point cloud to **PLY, glTF 2.0, and USDA** — the same real points,
  no invented surfaces — so you can open the scan in Blender, MeshLab, CloudCompare, Open3D, etc.

### People, vitals & BCI (proxies — never literal mind-reading)
- Vitals from RF: heart rate, breathing, HRV, sleep/apnea/cough proxies; blood-pressure estimate via
  pulse-transit-time; 17–24-joint body-pose skeleton fitting; WiFi-DensePose body mapping.
- **EEG/BCI** band-power metrics, Riemannian motor-intent, motor-imagery trial engine, LSL streaming.
- **Digital Resonance Twins**: a persistent, save/load/merge-able model of a person's *measured*
  signatures (HR/BR/gait/RF fingerprint + behavioral embedding). **It explicitly stores no thought
  content — `mind_content` is hard-wired to `None` everywhere.** It is a proxy, not a mind.
- **LifeFormAnimator**: animates a twin's skeleton from its measured gait/HR/breathing + tracked
  velocity (a behavioral proxy, not motion-capture).

### AI overseer & humanitarian intelligence
- An **AI overseer** (built on a consciousness/integration metric core) that perceives the full fused
  scene and produces an awareness state, decision log, and recommended actions. *"Consciousness" here
  is an integration metric — not a claim of sentience.*
- **Threat indicators** (distress, struggle) from grouping + motion + vitals — **recommend-only,
  evidence-cited, 0 false alarms on a nominal scene, always flagged UNCONFIRMED.** It never asserts a
  crime occurred; it flags patterns a human should review.
- **Pattern-of-life** deviation detection, **predictive convergence** forecasting (constant-velocity,
  no intent claimed), **long-term spectral memory** (flags new emitters / activity shifts),
  **human-readable threat narratives** with cited evidence, and **tamper-evident SHA-256 evidence
  packages** for forensic chain-of-custody.

### Planetary & astronomical context (real public data)
- **Planet map** (key `k`): real OpenStreetMap + satellite/terrain tiles + building footprints.
- **Observed sky**: a real star catalog + Sun/Moon/planets/galaxies with light-delay — genuine
  astronomical data overlay (honestly *public data*, not N.E.P.A.'s own active scan).

### Robustness, safety & validation
- **Adversarial red-team self-test**: injects jamming, spoofing, and node dropout and proves the
  system **degrades safely** (spoofed spikes caught by robust statistics, not trusted).
- **Default-deny safety/policy gate**: content/thought decode and individual real-time targeting are
  **hard-blocked**; humanitarian-use-only is enforced; every check is audited.
- **147 self-tests** re-run every 120 seconds; a central cross-validation ledger retests every
  inferred value against real data and keeps or discards it.

---

## 4. How close is it? — the honest scorecard

The program reports its own status along **three distinct dimensions you must not conflate**
(this is shown live in the Info/About panel, press `i`):

| Dimension | Score | Meaning |
|---|---:|---|
| **Software completeness** | **10 / 10** | Every *physically possible* capability in the plan is built, wired, and self-verified. |
| **Live-data fidelity** | **~7 / 10** | Hardware-gated. On a WiFi-only laptop you get a real but limited live picture. Rises **only** with real sensors/feeds (2nd receiver, phase-CSI, SDR, GPS, more data streams). |
| **Full dream (the total grand vision)** | **~4.7 / 10** | Physics-capped. The achievable envelope is mapped to its maximum; the impossible cores are excluded and never faked. |

**In plain words:** the *software* is essentially done — there is nothing physically achievable in
the plan that isn't implemented. What stands between this and the full planetary vision is **not more
code** — it's real hardware deployment, datacenter compute, and the laws of physics. The program is
the **closest honest software realization** of the vision, and it is explicit about exactly where the
ceiling is.

Against `plan2.md`'s own *"Success Criteria for 100% Goal Achievement"*:

- ✅ Global multi-instrument fusion → navigable persistent 3D world copy
- ✅ Digital resonance twins created, stored, animatable in the 3D scene
- ✅ AI overseer real-time threat/victimization detection with alerts
- ✅ Planetary-scale ingestion while staying honest about limits
- ✅ All features carry provenance + validation tests + ethical safeguards

All five are met **at the software-achievable ceiling.**

---

## 5. Global / galactic / universal scale — the truth

The goal names "global, galactic, and universal vision." Here is exactly how far software reaches —
stated honestly, because pretending otherwise would violate the prime directive:

### ✅ REAL right now (measured or honest public data)
- **Planet map** — real OSM + satellite/terrain tiles + building footprints.
- **Observed sky** — a real star catalog + Sun/Moon/planets/galaxies with light-delay. *This is
  genuine galactic/universal mapping* — but it comes from **public astronomy datasets**, not from
  N.E.P.A. actively scanning the cosmos.
- **Local RF world** — the actually-sensed scene (room → building) reconstructed from real instruments.

### 🟡 SIMULATION-FIRST (honestly flagged, flips to LIVE when real hardware/feeds attach)
- A **virtual mesh** of N instruments (`--virtual-mesh-size N`, flagged `VIRTUAL-MESH`).
- **Hierarchical geo-tiling** room → city → global, and a **satellite-ingest interface** ready for
  real feeds.

### 🔴 PHYSICS / HARDWARE / LEGAL-GATED — *not achievable in software alone, and never faked*
- A real global mesh of **millions of synchronized wideband sensors** (deployment, not code).
- **Orbital SAR / active galactic scanning** *by this system* (orbital hardware + data access).
- **Datacenter-scale trillions-of-correlations in real time** (compute infrastructure).
- **Seeing through metal / deep underground / across continents** at detail (violates physics at
  consumer power & aperture — penetration is capped by skin depth, reported `PENETRATION-LIMITED`).
- **Literal mind / consciousness decoding or copying** (physically impossible *and* privacy-forbidden;
  hard-blocked in code).

**Bottom line:** N.E.P.A. maps the *achievable* envelope to its maximum and **flags the rest**.
The vision document itself (`plan2.md`, lines 592–611) acknowledges these are blockers no amount of
code can remove. The program does not pretend to see what no instrument here can measure.

### v300++++ — Physics, Relativistic & Geodesy Upgrades (2026-09)

The program has been upgraded toward maximum physically honest, relativistic, and scale-correct
representation of reality. Every change is additive — no working features were removed. All 195
added/modified functions verified with **zero errors** (see `about.md` for the full proof).

**Exact SI constants:**
- `c = 299792458.0 m/s` (defined, exact) centralized in `PHYSICS_CONSTANTS` and used everywhere.
- 51+ scattered approximate `3e8` / `2.998e8` literals upgraded to the exact value across all
  physics classes (SAR, CSI, radar, tomography, Fresnel, DoA, multipath, orbit propagation).
- CODATA 2018 `G = 6.67430e-11`, `M_earth = 5.972168e24`, `mu_earth = 3.986004418e14`.

**Full WGS-84 ellipsoid geodesy** (replacing spherical approximations in geo-reference paths):
- `wgs84_lla_to_ecef` — exact WGS-84 ellipsoid → ECEF (survey-grade).
- `wgs84_ecef_to_enu` / `wgs84_lla_to_enu` — local ENU tangent plane (true-scale metres).
- `wgs84_geodetic_curvature_radius` — prime-vertical radius of curvature N(lat).
- `wgs84_vincenty_distance` / `wgs84_vincenty_bearing` — Vincenty's inverse formula for
  sub-metre geodesic distance and bearing on the ellipsoid.
- Wired into TrueView3D (`_azd`, `_enu`) and fused-world 3D for true ellipsoidal object placement.
- Spherical great-circle retained as fallback for near-antipodal points or missing geodetic data.
- `_render_selfcheck_wgs84()` — self-attests WGS-84 accuracy in-UI against known city references.

**Full special-relativity Doppler** (replacing first-order approximations):
- `relativistic_doppler_factor(beta)` — exact SR: `f_obs/f_src = sqrt((1-beta)/(1+beta))`.
- `relativistic_doppler_velocity(doppler_hz, f_src)` — exact inversion:
  `beta = (f_src^2 - f_obs^2) / (f_src^2 + f_obs^2)`.
- Wired into `RelativisticKineticPredictor` (satellite Doppler + SR+GR clock corrections) and
  the CSI micro-Doppler tracker (`Blah2MultiTargetTrackerNP76`).
- SR+GR satellite clock corrections preserved (GPS +38.6 us/day net advance verified).

**True-linear-scale 3D view mode:**
- `TRUEVIEW_LINEAR_SCALE` flag (toggle with `t` key) — switches the TrueView3D dome between
  log-depth (readable 7-decade default) and true-linear (100%-to-scale) range axis.
- `v` key prints voxel grid + physics Nyquist resolution info to the log.
- `_tv_range_to_display(d_m, RMAX, linear)` — unified helper for both modes.

**Adaptive Nyquist-scale voxel grid ("best vision clarity"):**
- Display voxel size adapts to the finest range resolution the active RF illuminators can
  resolve (`c/(2*BW)` of the best bandwidth), bounded to [0.05 m, 0.25 m] for memory safety.
- Preserves the original 0.25 m / 32³ grid when instruments cannot support finer (current
  state: FMCW 24 GHz 250 MHz → 0.60 m physics res → 0.25 m display preserved).
- `VOXEL_PHYSICS_RES_M` records the physics limit for UI honesty (oversampling for display
  clarity, not fabricated super-resolution).

**Disciplined time base (GNSS > NTP > wall clock):**
- `true_time()` — centralized time returning `(epoch_s, source_str)` where source is
  `'GNSS'` | `'NTP'` | `'WALLCLOCK'`. Always reports the source honestly.
- `register_gnss_time()` — called by `GPSDClient` when a GNSS TPV report arrives.
- `register_ntp_offset()` — called by `NetworkDiscoveryEngine` when NTP/chrony responds.
- No silent fallback to `0.0` — NTP failure preserves `None` (unknown), not `0.0` (in sync).

**Curvature-aware elevation (WGS-84):**
- `_true_elev_deg(d_m, h_m, obs_lat_deg)` — uses WGS-84 N(lat) when observer latitude is
  known, for ellipsoidal-accurate horizon distance and elevation angle. Negative = over horizon.

**Range resolution helpers (physics-bounded honesty):**
- `bistatic_range_res_m(bw)` — `c/(2*BW)` for round-trip radar/SAR.
- `oneway_tof_range_res_m(bw)` — `c/BW` for one-way CSI ToF (distinct from bistatic).
- `best_available_range_res_m(illuminators)` — finest `c/(2*BW)` from the active illuminator set.

### v301 — Simulation.py Integration, Wizard Tower & Kinetic Prediction (2026-09)

The complete `Simulation.py` (72,646 lines of particle/chemistry/physics/rendering code) has been
**embedded verbatim** inside `N.E.P.A.py` under `if _NEPA_SIM_RENDER_MODE:`. Normal launches never
execute a line of it. The embedded sim is **default OFF** and launched only on **F5** hotkey press
(or `--launch-sim` / `--sim-render <map>`). **F6** stops it.

**Wizard Tower — land-based multi-instrument sensing stack:**
- `WizardTowerInstrumentStack` — 30 instrument tiers, each a cross-reference channel, forming a
  30×30 cross-reference matrix. Superior to satellites for *local volume* (persistent dwell,
  multi-modal fusion) — never claims global coverage.
- Wired into the per-frame pipeline (`_v301_per_frame`) and runs while the main UI is idle.

**Kinetic Prediction Engine — see into the past and future:**
- `KineticPredictionEngine` — maintains frame history, harvests person blobs, real nodes, scalar
  channels, voxel energy, and counts.
- **Velocity Verlet** physics for both rewind (past reconstruction) and forward prediction:
  `x(t±dt) = x(t) ± v(t)·dt + 0.5·a(t)·dt²`
- 15×15 scalar-channel correlation matrix for cross-channel prediction.
- Rewind returns `[REWIND]`-tagged past states; prediction returns `[PREDICTED]`-tagged future states.
- Acceleration estimated from historical frames — captures accelerating motion correctly.

**Atomic reality render — the environment built from atoms:**
- F5 exports `nepa_reality_map.json` (voxel cells + entities + prediction + rewind, provenance-tagged
  `REAL` or `[ESTIMATED]`).
- The embedded sim loads the reality map and **replaces the default demo scene entirely** — only the
  measured environment is rendered, nothing else.
- Each measured voxel cell becomes an **Atom object** (with protons, neutrons, electrons as
  sub-particles). Element chosen by confidence: Silicon (Z=14) for concrete, Calcium (Z=20) for
  cement, Carbon (Z=6) for organic, Oxygen (Z=8) for dense air, Nitrogen (Z=7) for air.
- Tracked entities (persons) become **CHON biological atoms** (Carbon, Hydrogen, Oxygen, Nitrogen).
- Prediction and rewind overlays are rendered as atoms with `[PREDICTED]` / `[REWIND]` tags preserved.
- **Hardware capability check** before building: scales atoms-per-voxel by GPU VRAM and CPU cores.
  Warns when the machine is likely too weak: `"CPU-ONLY mode with N atoms — likely <1 FPS"`.
- **Lightweight atom creation** for structure atoms (map fixtures): skips quark creation, rejection
  sampling, orbital velocities, and bond assignment — ~100× faster than full atom creation.

**Performance optimizations (v301):**
- Cached `scipy.signal.butter` coefficients for all 5 filter bands (theta, gamma, beta, alpha, low-pass).
- Paced marching-cubes + blob detection to every 5th plot draw.
- Paced 3 spectrogram calculations to every 3rd plot frame.
- Paced heatmap bar rebuilds to every 3rd plot frame.
- Cached heatmap x-coordinates and vitals `twinx()` axis.
- Paced 3D voxel scatter to every 2nd draw frame.
- `set(particles)` built once per frame instead of twice.
- Cull pass uses squared distance instead of `np.linalg.norm` (skips sqrt).
- Double-slit experiment skipped when inactive.
- KPE correlation matrix rebuild throttled to every 10 frames.
- Wizard tower matrix recompute throttled to every 5 frames.

**Verification:** `python _v301_test.py` — tests kinetic history, 15×15 correlation matrix, rewind
accuracy, prediction accuracy, physics method tagging (`velocity_verlet`), accelerating-motion
prediction, wizard tower matrix, reality-map export, and the full `--sim-render` subprocess
round-trip (boots the embedded sim and asserts the `[NEPA-REALITY]` measured-environment load line
with atomic build). All tests pass.

---

## 6. Architecture & the V1→V63 capability stack

**One monolithic Python file.** No external sub-packages. It self-bootstraps its optional
dependencies. The internal structure is deliberately built like a distributed planetary system
(clean orchestrator / world-state / ledger interfaces) so it *could* be extracted into real
distributed nodes later — but today it runs efficiently in a single process.

Capabilities are added as an **additive subclass chain**: `NEPACapabilityExpansionPackV1` →
`...V50`, each pack inheriting the previous and adding a subsystem **without removing or replacing
prior code**. Highlights by era:

- **V20–V34 — Reality-Render stack:** live-enhance, dense-field render, photoreal/PBR surfaces,
  volumetric 3D, temporal coherence, motion flow, low-rank correlation + error correction, parallel
  compute.
- **V35–V47 — Perception & organization:** spectrum-as-light + sonification, multi-frame
  super-resolution, CLEAN deconvolution, correlation eigen-modes, tuneable multi-layer correlation,
  gestalt perceptual organization, object permanence/tracking, super-human-vision proof, AI-mind view.
- **V48–V50 — Grand-vision (plan2.md):** geo-reference (WGS84↔local↔voxel), penetration physics,
  total-spectrum overlay, digital resonance twins, virtual-mesh orchestrator, threat indicators,
  ethics/privacy enforcement, forensic timeline replay, lifeform animation, scan scheduling,
  glTF/USD export, long-term spectral memory, pattern-of-life, predictive causal reasoning, threat
  narratives, tamper-evident evidence packages, adversarial red-team suite, and a safety/policy gate.

**Performance note:** the heavy capability benchmarks (`verify()`) are memoized and run off the
per-frame path, so the live readout stays fast (~ms/frame) while the full stack remains continuously
self-verified.

---

## 7. The honesty model (provenance tiers)

Every displayed value carries one of these tags, and the rule is absolute — **absent data is shown
as empty/AWAITING, never invented:**

| Tier | Meaning |
|---|---|
| `MEASURED` / `LIVE` | Directly measured from a real instrument. |
| `INFERRED` | Derived, cross-validated, and retestable; tracked in the inference ledger. |
| `ESTIMATED` | A modeled estimate with stated assumptions. |
| `SIMULATED` | Produced by the internal simulator (e.g. `--simulate-hardware`). |
| `PROXY · DERIVED` | A stand-in built from measured signatures (e.g. resonance twins). |
| `SYNTHESIZED` | Visual-only detail (e.g. texture) — never treated as measured. |
| `PENETRATION-LIMITED` | Physics caps how deep this can see; beyond it is reported, not faked. |
| `GEO-APPROX` / `VIRTUAL-MESH` / `FORECAST·EXTRAPOLATED` / `CHANGE·STATISTICAL` / `INDICATOR·UNCONFIRMED` | Specific honest flags for geo conversion, simulated mesh nodes, forecasts, statistical changes, and unconfirmed threat indicators. |

Hard guarantees enforced in code: **thought content is never decoded** (`mind_content` is always
`None`), **RF-through-skull BCI is reported as impossible** (real EEG only), and the **acuity ceiling
is stated** (range resolution = c / 2·bandwidth — coverage and organization can be superhuman, but
photographic resolution within a band stays physics-bounded).

---

## 8. Installing & running

### Requirements
- **Python 3.10+**
- Core: `numpy`, `scipy`, `matplotlib` (the script self-bootstraps these and optional extras).
- Optional (gracefully degraded if absent): `onnxruntime`, `pywavelets`, `scikit-learn`,
  `opencv-python`, `open3d`, `torch`, `brainflow`, `pylsl`, `pyvista`, `paho-mqtt`, `Pillow`.

```bash
pip install -r requirements.txt        # core
# or everything:
pip install numpy scipy matplotlib onnxruntime pywavelets scikit-learn opencv-python
```

### Run

```bash
# Standard simulation run with the 3D world viewer:
python3 N.E.P.A.py --mode sim

# This project also ships a shell.nix — on Nix:
nix-shell --run "python3 N.E.P.A.py --mode sim"

# Headless / no world window:
python3 N.E.P.A.py --mode sim --no-world

# Prove it works (runs the full self-test suite and exits):
python3 N.E.P.A.py --self-test          # → 100/100 passed
```

### Quick honesty/feature demos
```bash
python3 N.E.P.A.py --physics-test           # prove frequency-bounce → range math vs known truth
python3 N.E.P.A.py --compound-benchmark     # honest end-to-end "X times better" on ground truth
python3 N.E.P.A.py --estimate-gain          # cumulative improvement % + amplification recommendations
python3 N.E.P.A.py --virtual-mesh-size 1000 # simulate a 1000-node virtual instrument mesh
python3 N.E.P.A.py --sonify-wav out.wav     # export a WAV of the spectrum sonification
```

---

## 9. The interface — tabs, keys, and views

A 3D world window (free-fly **WASD** camera) plus a matplotlib multi-tab dashboard. Key views:

| Key | View |
|---|---|
| `i` | **Info / About** — system reference, the honest 3-dimension scorecard, and the global/galactic/universal scale statement. |
| `/` | **Capabilities Atlas** — super-detailed per-subsystem documentation with live verified metrics. |
| `V` | **AI-Mind** — what the overseer perceives & "thinks": awareness state, decisions, super-vision proof. |
| `M` | **Mind-Proxy / Behavioral Overlay** — real measured vitals → plain-English behavioral *state* ("possible distress proxy"). NEURAL-PROXY·DERIVED; consent-gated; **not** thought-reading (`mind_content` stays `None`). |
| `r` | **Reality-Render** — the fused render stack output. |
| `l` | **Spectrum-Wave** — spectrum-as-light / waveform view. |
| `k` | **Planet Map** — real OSM / satellite / terrain tiles. |
| `1`–`9`, `0` | Individual sensor views. |
| `t` | **True-linear-scale toggle** — switches TrueView3D range axis between log-depth (readable 7-decade) and true-linear (100%-to-scale). |
| `v` | **Voxel/physics scale info** — prints current voxel grid resolution, scene range, and physics Nyquist limit to the log. |
| `F5` | **Launch reality simulation** — exports `nepa_reality_map.json` and launches the embedded Simulation.py as a subprocess. Renders the measured environment built from atoms. Default OFF. |
| `F6` | **Stop reality simulation** — terminates the embedded sim subprocess. |

---

## 10. Command-line flags

Run `python3 N.E.P.A.py --help` for the full list. Common ones:

| Flag | Purpose |
|---|---|
| `--mode sim` / `--mode udp` | Simulated source, or live UDP instrument input. |
| `--no-world` | Don't open the 3D world window (headless). |
| `--self-test` | Run the 147-check correctness/benchmark suite and exit. |
| `--simulate-hardware` | Register SIMULATED virtual instruments (every product watermarked SIMULATED). |
| `--ingest-port N` / `--csi-port N` | Accept real distributed sensor / ESP32-CSI data over the network. |
| `--mesh-node URL` | Run as a receiver-mesh node posting HMAC-signed observations. |
| `--llm-overseer` | Enable the Claude natural-language overseer (makes billable API calls; off by default). |
| `--lsl` / `--mqtt-host` / `--web-viewer` | Stream BCI bands (LSL), publish room state (MQTT/Home-Assistant), or serve the world over HTTP. |
| `--virtual-mesh-size N` | Simulate a virtual mesh of N instruments (flagged VIRTUAL-MESH). |
| `--estimate-gain` | Print the honest cumulative improvement estimate + amplification recommendations. |
| `--record-session` / `--replay-session` | Record/replay the per-frame snapshot stream. |
| `--seed N` | Seed all RNGs for a reproducible run. |

---

## 11. Getting more out of it (better data → better sight)

The single biggest lever is **more real instruments** — every one you connect flips a row from
simulated to live and *adds* a layer (the system never replaces one reading with another; it overlays
them). In rough order of impact:

1. **+ a 2nd receiver / buoy / phone** → enables real triangulation (accuracy scales with √N nodes).
2. **+ phase-CSI** (ESP32-CSI-Tool) → real channel sounding for the passive-radar pipeline.
3. **+ an SDR / KrakenSDR** → wideband spectrum + real direction-of-arrival.
4. **+ GPS / IMU** → real geo-referencing and SLAM.
5. **+ real EEG** (OpenBCI / Muse / LSL) → flips BCI metrics from proxy to measured.
6. **+ a GPU** → 10–100× rendering/correlation throughput.
7. **+ more public feeds** (satellite, astronomy) → richer planetary/cosmic context.

Almost all remaining headroom is **hardware**, because the software is already near the physical
ceiling for what the current instruments can measure.

---

## 12. Ethics, privacy & safety

This is humanitarian-first software, and the code enforces that operationally:

- **Content/thought decoding is hard-blocked** at the API level — it is impossible to ask the system
  to read minds; `mind_content` is always `None`.
- **Individual real-time targeting is blocked by default** policy; humanitarian-use-only is enforced;
  every access is audited.
- **Threat outputs are indicators, not accusations** — always flagged UNCONFIRMED, evidence-cited,
  recommend-review-by-a-human. The system never declares that a crime occurred.
- **Evidence is tamper-evident** (SHA-256 chain-of-custody) — it proves *integrity*, not *truth*.
- Wireless sensing of people is **heavily regulated or restricted** in most jurisdictions. Use this
  only where you are legally authorized and with consent. It is a research/defensive tool.

---

## 13. FAQ

**Can it really see through walls / underground / through metal?**
Through drywall and wood within physical skin-depth limits — yes, and that's real. 

**Is the 3D view literally to scale?**
The TrueView3D dome defaults to a log-depth axis (readable across 7 decades, from 1 m to
1000+ km on one dome). Press `t` to toggle to true-linear-scale mode (100%-to-scale, 1000 km
maps to the dome edge). The near-field inset always uses linear scale. All axes are honestly
labelled — log-scaled is never presented as literal scale.

**Does it use WGS-84 or a spherical Earth model?**
Both, in the right places. The v300++++ upgrade added full WGS-84 ellipsoid geodesy (ECEF/ENU
+ Vincenty's inverse formula for sub-metre distance/bearing) wired into all geo-reference
paths (TrueView3D, fused-world 3D). The spherical great-circle is retained as a fallback for
near-antipodal points or missing geodetic data. The program self-attests WGS-84 accuracy
in-UI via `_render_selfcheck_wgs84()`.

**Are the Doppler shifts relativistically correct?**
Yes. The v300++++ upgrade replaced the first-order Doppler approximation with the full
special-relativity formula `f_obs/f_src = sqrt((1-beta)/(1+beta))` in both the satellite
predictor and the CSI micro-Doppler tracker. The exact velocity inversion
`beta = (f_src^2 - f_obs^2) / (f_src^2 + f_obs^2)` is also used. For human-motion speeds the
difference from the classical approximation is negligible (~beta^2 ~ 1e-17), but the physics
is now relativistically exact.

**How is time disciplined?**
`true_time()` prefers GNSS-disciplined time (nanosecond-accurate when a GNSS receiver is
present via gpsd), then NTP-synced time (millisecond-accurate), then wall-clock
`time.time()`. The source is always reported (`GNSS` | `NTP` | `WALLCLOCK`) — no silent
fallback to `0.0`.

**How was all this verified?**
195 functions were exercised with real inputs in a zero-error verification suite. See
`about.md` for the complete proof output. The module also byte-compiles cleanly
(`python -m py_compile N.E.P.A.py` → exit 0).

---

*N.E.P.A. — turning the invisible electromagnetic world into visible, honest, actionable
understanding. Capability chain V1→V63 + v300++++ physics/relativistic/WGS-84 upgrades + v301
Simulation.py integration (wizard tower, kinetic prediction, atomic reality render) ·
147 self-tests + 195-function zero-error verification + v301 integration suite ·
prime directive: no false data, ever.*
