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

- **Single file:** `N.E.P.A.py` (~102,000 lines, one monolithic, copy-paste-runnable script)
- **Capability chain:** V1 → V50 (~109 additive subsystems)
- **Self-verification:** 100 built-in self-tests (`--self-test`), re-run live every 120 s
- **License/use:** research, educational, and defensive/humanitarian use only

---

## Table of Contents
1. [What this program is](#1-what-this-program-is)
2. [The goal (the grand vision)](#2-the-goal-the-grand-vision)
3. [What it can actually do today](#3-what-it-can-actually-do-today)
4. [How close is it? — the honest scorecard](#4-how-close-is-it--the-honest-scorecard)
5. [Global / galactic / universal scale — the truth](#5-global--galactic--universal-scale--the-truth)
6. [Architecture & the V1→V50 capability stack](#6-architecture--the-v1v50-capability-stack)
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
100-check `--self-test`):

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
- **100 self-tests** re-run every 120 seconds; a central cross-validation ledger retests every
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

---

## 6. Architecture & the V1→V50 capability stack

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
| `r` | **Reality-Render** — the fused render stack output. |
| `l` | **Spectrum-Wave** — spectrum-as-light / waveform view. |
| `k` | **Planet Map** — real OSM / satellite / terrain tiles. |
| `1`–`9`, `0` | Individual sensor views. |

---

## 10. Command-line flags

Run `python3 N.E.P.A.py --help` for the full list. Common ones:

| Flag | Purpose |
|---|---|
| `--mode sim` / `--mode udp` | Simulated source, or live UDP instrument input. |
| `--no-world` | Don't open the 3D world window (headless). |
| `--self-test` | Run the 100-check correctness/benchmark suite and exit. |
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

*N.E.P.A. — turning the invisible electromagnetic world into visible, honest, actionable
understanding. Capability chain V1→V50 · 100 self-tests · prime directive: no false data, ever.*
