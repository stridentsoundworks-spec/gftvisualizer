README 
# ✦ Quantum Fields

**An immersive, audio-reactive particle simulation exploring the visual aesthetics of quantum field theory.**

[![Three.js](https://img.shields.io/badge/Three.js-r182-black?logo=three.js)](https://threejs.org/)
[![WebGL](https://img.shields.io/badge/WebGL-2.0-red)](https://www.khronos.org/webgl/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Software](https://perplexity.ai)]

[![Live Demo](https://img.shields.io/badge/Demo-Live-brightgreen)](https://qftvisualizer.netlify.app)


<p align="center">
  <img src="assets/preview.gif" alt="Quantum Fields Preview" width="800">
</p>

## Overview

Quantum Fields is a real-time WebGL visualization that renders 250,000+ particles simulating the behavior of quantum fields. The particles respond dynamically to audio input—either from uploaded music files or live microphone input—creating mesmerizing visual representations of sound through physics-inspired motion.

## ✨ Features

### Particle System
- **250,000+ GPU-accelerated particles** using custom GLSL shaders
- **Curl noise flow fields** for fluid, organic motion
- **Simplex noise** for natural turbulence patterns
- **Multi-layer particle system** with primary and secondary fields

### Audio Reactivity
- **7-band frequency analysis**: Sub-bass, Bass, Low-mid, Mid, High-mid, High, Ultra-high
- **Beat detection** with dynamic threshold adaptation
- **Spectral centroid & flux** analysis for nuanced responses
- **Intelligent bass gate** with calibration, attack/release, and compression
- **File playback** with full transport controls (play, pause, seek, loop)
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

### Visual Effects Pipeline
- **God Rays** — Volumetric light scattering from bright particles
- **Depth of Field** — Cinematic bokeh blur with auto-focus
- **Particle Trails** — 50 independent trailing particles with vortex motion
- **Lens Flares** — Procedural flares with chromatic ghosts and halos
- **Bloom** — Unreal Engine-style HDR bloom
- **Afterimage/Trails** — Configurable motion persistence
- **Anamorphic Flares** — Horizontal streak effects on bright spots
- **Chromatic Aberration** — Beat-reactive color fringing
- **Film Grain** — Optional analog texture
- **Vignette** — Dynamic edge darkening

### Interactions
- **Mouse repulsion** — Particles react to cursor with velocity-based influence
- **Camera shake** — Beat-synchronized camera movement
- **Orbital controls** — Smooth rotation, zoom, and pan
- **Auto-rotation** — Speed modulated by audio energy

## 🚀 Getting Started

### Quick Start
1. Download `quantum_v9_aurora.html`
2. Open in a modern browser (Chrome, Firefox, Edge, Safari)
3. Click "Choose Audio" to load a music file, or "Microphone" for live input
4. Enjoy the visualization!

### Local Development
```bash
# Clone the repository
git clone https://github.com/yourusername/quantum-fields.git
cd quantum-fields

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
The visualization includes a comprehensive control panel:

- **Audio Sensitivity** — Global audio response multiplier
- **Physics Engine** — Field type, density, vortex, pulse intensity
- **Bass Gate** — Threshold, attack, release, ratio controls
- **✨ New Effects** — God rays, DOF, lens flares, particle trails
- **Optics** — Bloom, trails, chromatic aberration, grain, shake

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
- **Target**: 60 FPS on dedicated GPUs
- **Particle count**: Adjustable via density slider (0-100%)
- **Pixel ratio**: Capped at 2x for performance
- **Draw calls**: Optimized single-draw particle system

## 📁 Project Structure

```
quantum-fields/
├── quantum_v9_aurora.html    # Main application (single file)
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

### v9 — Aurora (Current)
- ✨ Added God Rays volumetric lighting
- ✨ Added Depth of Field with auto-focus
- ✨ Added Particle Trail system (50 trails)
- ✨ Added Lens Flare (3D + post-process)
- ✨ Added Vignette + Glow enhancement
- 🎮 New "F" key to toggle DOF
- 🎛️ New GUI folder for effects controls

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

- [Three.js](https://threejs.org/) team for the incredible 3D library
- [Stefan Gustavson](https://github.com/stegu/webgl-noise) for simplex noise implementation
- The WebGL and creative coding community

---

<p align="center">
  Made with ✨ and WebGL
</p>
