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

Quantum Fields is a real-time WebGL visualization that renders **285,000 particles** (250K primary + 35K secondary) simulating the behavior of quantum fields. Set against a procedural space nebula backdrop, the particles respond dynamically to audio input—either from uploaded music files or live microphone input—creating mesmerizing visual representations of sound through physics-inspired motion.

**[▶ Launch Live Demo](https://qftvisualizer.theobharvey.com)**

## ✨ Features

### Particle System
- **285,000 GPU-accelerated particles** — 250K primary + 35K secondary shell
- **Curl noise flow fields** for fluid, organic motion
- **Simplex noise** for natural turbulence patterns
- **Multi-layer particle system** with independent primary and secondary behaviors
- **Force Network** — Dynamic connections between nearby particles

### Audio Reactivity
- **7-band frequency analysis**: Sub-bass, Bass, Low-mid, Mid, High-mid, High, Ultra-high
- **Beat detection** with dynamic threshold adaptation
- **Onset detection** with configurable punch sensitivity
- **Spectral centroid & flux** analysis for nuanced responses
- **Intelligent bass gate** with threshold, attack/release controls
- **Audio-reactive camera** — Camera movement synced to music energy
- **File playback** with full transport controls (play, pause, seek)
- **Live microphone** input support

### Quantum Field Types
| Field | Characteristics |
|-------|-----------------|
| **Photon (EM)** | Cyan/blue palette, balanced flow |
| **Gluon (Strong)** | Magenta/violet, high turbulence |
| **Higgs (Mass)** | Orange/gold, slow & massive |
| **Gravity** | White/blue, gentle curves |
| **Dark Energy** | Deep purple, ethereal expansion |
| **Neutrino** | Green/cyan, fast & chaotic |

### Environment
- **Space Nebula** — Procedural nebula background that breathes with audio
- **Force Network** — Dynamic particle connections with configurable range/opacity
- **Particle Trails** — 50 independent trailing particles with vortex motion

### Visual Effects Pipeline
- **God Rays** — Volumetric light scattering with beat-reactive intensity
- **Radial Depth of Field** — Custom bokeh blur with focus ring control
- **Lens Flares** — Dual-layer procedural flares (3D + post-process)
- **Bloom** — Unreal Engine-style HDR bloom
- **Motion Blur** — Configurable afterimage persistence
- **Anamorphic Flares** — Horizontal streak effects on bright spots
- **Chromatic Aberration** — Beat-reactive color fringing
- **Film Grain** — Optional analog texture overlay
- **Vignette** — Dynamic beat-pulsing edge darkening

### Interactions
- **Mouse repulsion** — Particles react to cursor with velocity-based influence
- **Camera shake** — Beat-synchronized camera movement
- **Orbital controls** — Smooth rotation, zoom, and pan
- **Auto-rotation** — Speed modulated by audio energy

## 🚀 Getting Started

### Quick Start
1. Visit **[qftvisualizer.netlify.app](https://qftvisualizer.netlify.app)** — no installation required
2. Click "Choose Audio" to load a music file, or "Microphone" for live input
3. Explore the 6 quantum field presets and adjust effects in the GUI
4. Press `F` to toggle cinematic depth of field

### Local Development
```bash
# Clone the repository
git clone https://github.com/stridentsoundworks-spec/gftvisualizer.git
cd gftvisualizer

# Serve locally (required for ES modules)
npx serve .
# or
python -m http.server 8000

# Open http://localhost:8000 in your browser
```

### Requirements
- Modern browser with WebGL 2.0 support
- Hardware-accelerated graphics recommended
- Audio input (file or microphone)

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

### GUI Panel
The visualization includes a comprehensive control panel with 7 folders:

| Folder | Controls |
|--------|----------|
| **Main** | Field Type, Audio Sensitivity, Density, Time Flow |
| **🌌 Environment** | Space Nebula, Force Network, Particle Trails |
| **🎥 Camera & Lens** | Lens Flare, Depth of Field, Focus Ring, Camera Shake |
| **✨ Post Processing** | Bloom, Motion Blur, Chromatic, Anamorphic, God Rays, Film Grain |
| **⚙️ Physics** | Vortex Strength, Pulse Intensity |
| **🎤 Audio Gate** | Enable, Threshold, Attack, Release |
| **🚀 Enhancement Pack** | Onset Punch, Audio Camera, Terrain Height, Auto Quality, FPS Monitor |

## 🔧 Technical Details

### Architecture
```
┌─────────────────────────────────────────────────────────┐
│                    Audio Input                          │
│              (File / Microphone)                        │
└─────────────────┬───────────────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────────────┐
│              Web Audio API Analyzer                     │
│   ┌─────────┐ ┌──────────┐ ┌─────────┐ ┌────────────┐   │
│   │ FFT     │ │ Band     │ │ Beat    │ │ Spectral   │   │
│   │ Analysis│ │ Splitting│ │ Detect  │ │ Analysis   │   │
│   └─────────┘ └──────────┘ └─────────┘ └────────────┘   │
└─────────────────┬───────────────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────────────┐
│              GLSL Vertex Shader                         │
│   ┌─────────┐ ┌──────────┐ ┌─────────┐ ┌────────────┐   │
│   │ Curl    │ │ Vortex   │ │ Beat    │ │ Mouse      │   │
│   │ Noise   │ │ Motion   │ │ Pulses  │ │ Repulsion  │   │
│   └─────────┘ └──────────┘ └─────────┘ └────────────┘   │
└─────────────────┬───────────────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────────────┐
│           Post-Processing Pipeline                      │
│                                                         │
│   Render → Afterimage → Bloom → God Rays → Lens Flare   │
│         → Anamorphic → Chromatic → DOF → Vignette       │
│         → Grain → Output                                │
└─────────────────────────────────────────────────────────┘
```

### Dependencies
All dependencies are loaded via CDN (no build step required):

| Library | Version | Purpose |
|---------|---------|---------|
| [Three.js](https://threejs.org/) | r182 | 3D rendering engine |
| [lil-gui](https://lil-gui.georgealways.com/) | 0.19.1 | Control panel UI |

### Performance
- **Target**: 30-60 FPS (configurable via Enhancement Pack)
- **Adaptive quality**: Automatically adjusts to maintain target FPS
- **Particle count**: Adjustable via density slider (1.7%-14%)
- **Pixel ratio**: Capped at 2x for performance
- **Real-time monitoring**: FPS counter in GUI

## 📁 Project Structure

```
gftvisualizer/
├── index.html                # Main application (single file)
├── README.md                 # This file
├── LICENSE                   # MIT License
└── assets/
    └── preview.gif           # Preview animation
```

## 🎨 Customization

### Adding New Field Types
```javascript
const FIELD_TYPES = {
    'Your Field': {
        c1: '#ff0000',  // Primary color
        c2: '#00ff00',  // Secondary color  
        c3: '#0000ff',  // Accent color
        s: 1.5,         // Noise scale
        curl: 1.2,      // Curl strength
        sz: 1.8         // Particle size
    }
};
```

### Modifying Shaders
The vertex and fragment shaders are embedded in the HTML file. Key uniforms:
- `uTime` — Animation time
- `uBass`, `uMid`, `uHigh` — Frequency bands
- `uBeatEnergy` — Beat detection envelope
- `uVortexStrength` — Rotational force
- `uPulseIntensity` — Radial wave strength

## 📜 Changelog

### Nebula v1 (Current) — December 2025
- 🌌 **Space Nebula** — Procedural nebula background with audio reactivity
- 🔗 **Force Network** — Dynamic particle connections with configurable range/opacity
- 🎯 **Radial DOF** — Custom depth of field with focus ring and bokeh controls
- 🚀 **Enhancement Pack v2.0**:
  - Onset detection with punch sensitivity
  - Audio-reactive camera movement
  - Waveform terrain mode
  - Adaptive quality system with FPS targeting
- 🎨 **35K Secondary Particles** — Independent shell layer with high-frequency response
- 📊 **Real-time FPS monitoring** in GUI
- 🎛️ Reorganized GUI with 7 control folders

### v9 — Aurora
- ✨ God Rays volumetric lighting
- ✨ Depth of Field with auto-focus
- ✨ Particle Trail system (50 trails)
- ✨ Lens Flare (3D + post-process)
- ✨ Vignette + Glow enhancement
- 🎮 "F" key to toggle DOF

### v8
- 🎵 Full audio playback controls
- 🎚️ Bass gate with auto-calibration
- 🎨 6 quantum field presets
- 📸 Screenshot functionality
- 🖥️ Fullscreen support

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- The Perplexity Team (https://perplexity.ai/blog)
- The Anthropic Team (https://anthropic.com) 
- George Nachman & Team (iTerm2)
- [Three.js](https://threejs.org/) team for the incredible 3D library
- [Stefan Gustavson](https://github.com/stegu/webgl-noise) for simplex noise implementation
- The WebGL and creative coding community

---

<p align="center">
  Made with ✨ and WebGL
</p>
