# ✦ Quantum Fields

**An immersive, audio-reactive particle simulation exploring the visual aesthetics of quantum field theory.**

[![Three.js](https://img.shields.io/badge/Three.js-r182-black?logo=three.js)](https://threejs.org/)
[![WebGL](https://img.shields.io/badge/WebGL-2.0-red)](https://www.khronos.org/webgl/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Software](https://img.shields.io/badge/Powered_By-Perplexity-gold)](https://perplexity.ai)
[![Live Demo](https://img.shields.io/badge/Demo-Live-brightgreen)](https://qftvisualizer.theobharvey.com)

<p align="center">
  <img src="assets/preview.gif" alt="Quantum Fields Preview" width="800">
</p>

## Overview

Quantum Fields is a real-time WebGL visualization that renders **285,000 particles** across three independent layers, each reading a different slice of the audio spectrum. The particle field, outer atmospheric shell, force network, and crawling light agents all respond to music simultaneously — creating a living, breathing representation of sound through physics-inspired motion.

**[▶ Launch Live Demo](https://qftvisualizer.theobharvey.com)**

---

## ✨ Features

### Three-Layer Particle System

#### Primary Field (250K particles)
- **Curl noise flow fields** for fluid, organic motion driven by low-mid and spectral flux
- **Vortex rotation** modulated by bass energy
- **Mouse repulsion** with velocity-based influence radius
- **Beat pulse rings** — radial waves emanating from centre on every detected beat
- **Onset energy punch** — transient attacks push particles outward instantly
- **Waveform terrain mode** — particles reshape into a frequency-reactive landscape

#### Secondary Shell (25K particles)
- Lives in the **outer atmospheric halo** (65–110% of field radius)
- Runs at a **slower timescale** than the core — atmospheric drift, not particle chaos
- **Two-scale noise**: sub-bass and low-mid drive large slow drifts; high frequencies and spectral flux add sharp turbulence on top
- **Vortex coupling** — the shell rotates in sync with the main field's vortex on bass hits
- **Onset scatter** — transients push the halo outward in a visible burst
- **Sub-bass breathing** — slow sinusoidal expansion/contraction driven by the lowest frequencies
- **Ultra-high sparkle** — 15% of particles flicker rapidly on cymbal and hi-hat content
- **Spectral centroid hue shift** — shell colour drifts between field palettes with frequency content
- **Depth haze** — particles behind the field centre fade toward black for genuine 3D atmosphere

#### Force Network
- **500 tracked particles** checked pairwise for proximity connections, up to **800 line segments**
- **Evolving topology** — tracked particle set refreshes every ~2 seconds; the network rewires itself continuously
- **Dynamic density** — connection count scales with `mid + highMid` energy; sparse when quiet, dense when the mix is full
- **Centre-bright** — lines near the field core are up to 40% brighter than outer edges
- **Per-line alpha** driven by `highMid` (presence/attack range) — snares and guitar attacks light up the network
- **Beat pulse flash** — all connections briefly brighten simultaneously on every detected beat
- **Spectral hue shift** — line colour blends between field palettes with spectral centroid
- **Threshold breathing** — connection range expands with bass, tightens on high-mid energy

#### Network Crawlers
- **24 independent light agents** that trace slow paths through the force network topology
- Each crawler has a **fading tail** (up to 10 world-space distance-sampled points) — genuine slow traces, not lightning bolts
- **Speed reactive to `highMid` and beatEnergy** — crawlers surge on attack then settle back
- Crawlers **pick the nearest connected neighbour** at each node and keep moving — continuous, never stopping
- **Occasional teleport** keeps agents distributed across the field rather than clustering
- **Spectral hue** — crawler colour tracks `c1→c3` of the current field, shifted by spectral centroid
- Only visible when **audio is actively playing** — disappear cleanly when silent

---

### Audio Analysis

- **7-band frequency analysis** tuned to instrument anatomy:

| Band | Range | What it drives |
|------|-------|----------------|
| Sub-bass | 50–120 Hz | Kick drum fundamental, shell breathing, sub-bass drift |
| Bass | 120–200 Hz | Bass guitar body, vortex rotation |
| Low-mid | 200–450 Hz | Warmth, large shell drift, vertical motion |
| Mid | 450–2000 Hz | Vocals, guitars, network density |
| High-mid | 2000–3500 Hz | Attack/presence, network line alpha, crawler speed |
| High | 3500–12000 Hz | Shell turbulence, particle sparkle |
| Ultra-high | 12000–20000 Hz | Shell sparkle, fine turbulence |

- **Beat detection** with dynamic threshold adaptation (threshold: 0.15, decay: 0.93)
- **Onset detection** — spectral flux derivative for sharp transient response
- **Spectral centroid & flux** for hue shifting and turbulence
- **Intelligent bass gate** with threshold, attack/release, auto-calibration
- **GainNode pre-boost** — 3× signal amplification before FFT for BlackHole/loopback input
- **FFT smoothing**: 0.65 (crisper transient response vs default 0.8)
- **Audio-reactive camera** — subtle movement synced to music energy
- **File playback** with full transport controls (play, pause, seek)
- **Live microphone/loopback** input with device selection

---

### Quantum Field Types

| Field | Palette | Character |
|-------|---------|-----------|
| **Photon (EM)** | Cyan / deep blue / white | Balanced flow, clean structure |
| **Gluon (Strong)** | Magenta / violet / amber | High turbulence, strong vortex |
| **Higgs (Mass)** | Amber / orange / yellow | Slow and massive, wide particles |
| **Gravity** | White / blue / violet | Gentle curves, minimal chaos |
| **Dark Energy** | Deep purple / violet / magenta | Ethereal, expansive |
| **Neutrino** | Teal / cyan / green | Fast and chaotic, minimal mass |
| **Waveform Terrain** | Pink / teal / indigo | Frequency-reactive terrain mode |

---

### Dynamic UI Theming

The **entire UI recolours** with the selected field — smoothly interpolated at 60fps:
- Configure button border, background and text
- GUI panel border, title, folder highlights
- Slider tracks and glow
- Checkboxes
- Audio controls bar and progress gradient
- Enter button
- Overlay title gradient

Accent colours are luminance-clamped so dark fields (e.g. Dark Energy) always remain readable.

---

### Visual Effects Pipeline

- **Bloom** — Unreal Engine-style HDR bloom (strength: 0.6, threshold: 0.25)
- **Motion Blur** — Configurable afterimage/trails persistence
- **God Rays** — Volumetric light scattering with beat-reactive intensity
- **Radial Depth of Field** — Custom bokeh blur with focus ring control
- **Lens Flares** — Dual-layer procedural flares (3D + post-process)
- **Anamorphic Flares** — Horizontal streak effects on bright spots
- **Chromatic Aberration** — Beat-reactive colour fringing
- **Film Grain** — Optional analog texture overlay
- **Vignette** — Dynamic beat-pulsing edge darkening
- **ACES Filmic Tone Mapping** — Cinema-grade exposure curve

---

## 🚀 Getting Started

### Quick Start
1. Visit **[qftvisualizer.theobharvey.com](https://qftvisualizer.theobharvey.com)**
2. Click **Enter** to activate mic/loopback input — or load an audio file via the controls bar
3. Explore the 7 quantum field presets
4. Open **✦ Configure** to adjust effects, physics, and audio settings
5. Press `F` to toggle cinematic depth of field

### BlackHole / System Audio (macOS)
The visualizer includes a pre-boost gain stage specifically for BlackHole loopback input. Set up a Multi-Output Device in Audio MIDI Setup routing your system audio through BlackHole, then click Enter — no extra configuration needed.

### Local Development
```bash
git clone https://github.com/stridentsoundworks-spec/gftvisualizer.git
cd gftvisualizer

# Serve locally (required for ES modules)
npx serve .
# or
python -m http.server 8000

# Open http://localhost:8000
```

### Requirements
- Modern browser with WebGL 2.0 support (Chrome, Firefox, Safari 16+)
- Hardware-accelerated graphics recommended
- Audio input (file or microphone/loopback)

---

## 🎮 Controls

### Keyboard
| Key | Action |
|-----|--------|
| `Space` | Play / Pause audio |
| `F` | Toggle Depth of Field |
| `+` / `=` | Zoom in |
| `-` / `_` | Zoom out |
| `0` | Reset zoom |

### Mouse
| Action | Effect |
|--------|--------|
| **Drag** | Rotate camera |
| **Scroll** | Zoom in/out |
| **Move** | Particle repulsion field |

### GUI Panel (✦ Configure)
| Folder | Controls |
|--------|----------|
| **Main** | Field Type, Audio Sensitivity, Density, Time Flow |
| **🌌 Environment** | Space Nebula, Force Network, Network Crawlers, Particle Trails |
| **🎥 Camera & Lens** | Lens Flare, Depth of Field, Focus Ring, Camera Shake |
| **✨ Post Processing** | Bloom, Motion Blur, Chromatic, Anamorphic, God Rays, Film Grain |
| **⚙️ Physics** | Vortex Strength, Pulse Intensity |
| **🎤 Audio Gate** | Enable, Threshold, Attack, Release |
| **🚀 Enhancement Pack** | Onset Punch, Audio Camera, Terrain Height, Auto Quality, FPS Monitor |

---

## 🔧 Technical Details

### Architecture

```
┌─────────────────────────────────────────────────────────┐
│              Audio Input (File / Mic / Loopback)        │
│              GainNode (3× pre-boost)                    │
└─────────────────┬───────────────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────────────┐
│              Web Audio API Analyzer (FFT 4096)          │
│   ┌──────────┐ ┌──────────┐ ┌─────────┐ ┌───────────┐  │
│   │ 7-Band   │ │  Beat    │ │ Onset   │ │ Spectral  │  │
│   │ Splitter │ │ Detect   │ │ Detect  │ │ Analysis  │  │
│   └──────────┘ └──────────┘ └─────────┘ └───────────┘  │
└─────────────────┬───────────────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────────────┐
│                  Three-Layer Render                     │
│   ┌─────────────┐ ┌────────────┐ ┌────────────────────┐ │
│   │ Primary     │ │ Secondary  │ │ Force Network +    │ │
│   │ 250K pts    │ │ Shell 25K  │ │ Crawlers           │ │
│   │ Curl noise  │ │ Atmosphere │ │ 500 tracked pts    │ │
│   │ GLSL shader │ │ GLSL shader│ │ 24 light agents    │ │
│   └─────────────┘ └────────────┘ └────────────────────┘ │
└─────────────────┬───────────────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────────────┐
│           Post-Processing Pipeline                      │
│  Render → Afterimage → Bloom → God Rays → Lens Flare   │
│        → Anamorphic → Chromatic → DOF → Vignette       │
│        → Grain → Output                                 │
└─────────────────────────────────────────────────────────┘
```

### Dependencies
All loaded via CDN — no build step required:

| Library | Version | Purpose |
|---------|---------|---------|
| [Three.js](https://threejs.org/) | r182 | 3D rendering engine |
| [lil-gui](https://lil-gui.georgealways.com/) | 0.19.1 | Control panel UI |

### Performance
- **Target**: 60 FPS
- **Pixel ratio**: Capped at device DPR (max 2×)
- **Antialiasing**: Hardware MSAA enabled
- **Particle count**: Adjustable via density slider (1.7%–14%)
- **Adaptive quality**: Optional FPS-targeting system
- **Force network**: O(n²) CPU pairwise with 500-particle subset per frame

---

## 📁 Project Structure

```
gftvisualizer/
├── index.html     # Entire application — single self-contained file
├── README.md      # This file
└── LICENSE        # MIT License
```

---

## 🎨 Customization

### Adding a Field Type
```javascript
const FIELD_TYPES = {
    'Your Field': {
        c1:   '#ff0000',  // Primary colour
        c2:   '#00ff00',  // Secondary colour
        c3:   '#0000ff',  // Accent colour
        sc1:  '#ff6666',  // Secondary shell colour 1
        sc2:  '#66ff66',  // Secondary shell colour 2
        s:    1.5,        // Noise scale
        curl: 1.2,        // Curl strength
        sz:   2.8         // Particle base size
    }
};
```

### Key Shader Uniforms
| Uniform | Description |
|---------|-------------|
| `uTime` | Animation time |
| `uSubBass` … `uUltraHigh` | 7 frequency band values (0–1) |
| `uBeatEnergy` | Beat detection envelope |
| `uOnsetEnergy` | Transient onset envelope |
| `uSpectralCentroid` | Weighted frequency centre (0–1) |
| `uSpectralFlux` | Rate of spectral change |
| `uVortexStrength` | Rotational force multiplier |
| `uPulseIntensity` | Radial wave amplitude |

---

## 📜 Changelog

### Crawler Update — April 2026
- 🕷️ **Network Crawlers** — 24 light agents trace slow deliberate paths through the force network with fading tails, audio-reactive speed, and spectral hue
- 🎨 **Full dynamic UI theming** — entire interface (buttons, GUI, sliders, progress bar) recolours with selected field; luminance-clamped for readability
- 🔊 **Audio system retuned** — GainNode pre-boost for BlackHole/loopback, rebalanced 7-band frequency ranges, sharper beat detection and FFT smoothing
- 🌐 **Force network overhauled** — evolving topology, dynamic density, per-line highMid reactivity, spectral hue shift, centre-bright lines
- 🌌 **Secondary shell rewritten** — full 7-band reactivity, onset scatter, vortex coupling, depth haze, sub-bass breathing, ultra-high sparkle
- 💅 **Visual clarity pass** — particle sizes increased, bloom tuned, antialiasing enabled

### Nebula v1 — December 2025
- 🌌 Space Nebula procedural background
- 🔗 Force Network with configurable range/opacity
- 🎯 Radial DOF with focus ring and bokeh
- 🚀 Enhancement Pack v2.0 (onset detection, audio camera, waveform terrain, adaptive quality)
- 🎨 35K secondary particle shell
- 🎛️ Reorganised GUI with 7 folders

### v9 — Aurora
- ✨ God Rays volumetric lighting
- ✨ Particle Trail system (50 trails)
- ✨ Lens Flare (3D + post-process)
- ✨ Vignette + glow enhancement

### v8
- 🎵 Full audio playback controls
- 🎚️ Bass gate with auto-calibration
- 🎨 6 quantum field presets
- 📸 Screenshot functionality
- 🖥️ Fullscreen support

---

## 🤝 Contributing

Contributions are welcome. For major changes please open an issue first.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes
4. Push and open a Pull Request

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

## 🙏 Acknowledgments

- [Perplexity AI](https://perplexity.ai) — built collaboratively with Weave
- [Anthropic](https://anthropic.com) — Claude
- [Three.js](https://threejs.org/) team
- [Stefan Gustavson](https://github.com/stegu/webgl-noise) — simplex noise implementation
- The WebGL and creative coding community

---

<p align="center">
  Made with ✦ and WebGL
</p>
