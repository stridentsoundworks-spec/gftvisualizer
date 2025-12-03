
# ⚛️ Quantum Visuals: Audio-Reactive Quantum Field Simulator

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![WebGL](https://img.shields.io/badge/WebGL-Three.js-black)
![Version](https://img.shields.io/badge/version-6.1-purple)
![Status](https://img.shields.io/badge/status-Stable-green)

**A High-Definition, interactive 3D simulation of Quantum Field Theory (QFT) that reacts to audio analysis in real-time.**

This project visualizes the concept of vacuum fluctuations and particle excitations using GPU-accelerated fluid dynamics. 
It renders up to **275,000 interactive particles** in the browser using custom GLSL shaders, 
simulating the behavior of different quantum fields (Electromagnetic, Strong Force, Higgs, Gravity, Dark Energy, and Neutrino).

---

## 🆕 What's New in v4.5

### 🎛️ Full Playback Controls
- **Play/Pause** - Full transport controls with spacebar shortcut
- **Progress Bar** - Visual timeline with click-to-seek functionality
- **Track Switching** - Load new audio files without refreshing the page
- **Time Display** - Current position and total duration

### 🔊 Advanced Bass Gate System
The bass gate provides consistent audio reactivity by filtering noise and controlling signal dynamics:
- **Auto-Calibrating Noise Floor** - Automatically adapts to your audio source
- **Hysteresis Threshold** - Prevents rapid gate chattering
- **Attack/Release Envelope** - Smooth transitions when gate opens/closes
- **Soft Knee Compression** - Prevents clipping on loud transients

> **Tip:** Enable bass gate for music to make the simulator pulse cleanly. Disable for voice/mic input to reduce the pulse effect.

### 🔭 Enhanced Zoom & Navigation
- **Scroll Wheel Zoom** - Smooth zoom with configurable limits (25-200 units)
- **Keyboard Zoom** - `+`/`-` keys for fine control, `0` to reset view
- **Zoom Indicator** - Real-time percentage display
- **Zoom-Compensated Particles** - Particles scale appropriately at all distances
- **Click to Pulse in voice mode** - Clicks and touches in voice mode pulse the field (Satisfying af and fun)

---

## 🚀 Live Demo

**[DEMO 🔗](https://qftvisualizer.netlify.app)**

*(Note: Microphone access is required for the live audio reactivity feature)*

---

## ✨ Key Features

### 🎨 High-Fidelity Visuals
- **Dual-Layer Particle System:** Renders 250k primary + 25k secondary particles for depth
- **Cinematic Post-Processing Stack:**
  - Optical Bloom with dynamic intensity
  - Anamorphic Lens Flares (horizontal light streaks)
  - Chromatic Aberration (beat-reactive)
  - Film Grain for atmosphere
  - CRT Scanline overlays
- **Particle Trails:** Afterimage processing for "bubble chamber" trail effects
- **Fresnel Rim Lighting:** Particles glow at view-angle edges
- **Atmospheric Perspective:** Depth-based color desaturation

### 🔊 Audio Intelligence

#### 7-Band Frequency Analysis (Can be modified to preference)
| Band | Frequency Range | Visual Effect |
|------|-----------------|---------------|
| Sub-Bass | 20-60 Hz | Field breathing, deep pulses |
| Bass | 60-250 Hz | Shockwaves, vortex rotation |
| Low-Mid | 250-500 Hz | Turbulence modulation |
| Mid | 500-2000 Hz | Time dilation, rotation speed |
| High-Mid | 2000-4000 Hz | Color mixing intensity |
| High | 4000-8000 Hz | Particle sparkle, shimmer |
| Ultra-High | 8000-16000 Hz | Color tinting, micro-detail |

#### Beat Detection System
- **Onset Detection** - Identifies sudden transients in the audio
- **Dynamic Thresholding** - Adapts to track energy levels
- **Peak History Analysis** - Uses ~1 second of history for accuracy
- **Spectral Flux Tracking** - Detects rapid frequency changes
- **Spectral Centroid** - Measures audio "brightness" for color shifts

#### Input Modes
- **Audio File Upload** - Load MP3, WAV, FLAC, or any browser-supported format
- **Live Microphone** - Real-time visualization of ambient audio
- **Seamless Switching** - Change sources without page refresh

### ⚗️ Physics Engine
- **Multi-Octave Curl Noise:** Layered fluid dynamics with FBM (Fractal Brownian Motion)
- **Dual Vortex System:** Separate sub-bass and bass-driven rotation patterns
- **Y-Axis Spiral Motion:** Vertical particle spiraling based on mid frequencies
- **Multi-Ring Beat Pulses:** Two phase-offset expanding rings on detected beats
- **Interactive Collider:** Mouse cursor displaces particles with velocity-based intensity

### 🌌 6 Field Presets

| Field | Colors | Behavior |
|-------|--------|----------|
| **Photon (EM)** | Cyan / Blue / White | Fluid, fast-moving, clean |
| **Gluon (Strong)** | Magenta / Purple / Orange | Chaotic, high-turbulence |
| **Higgs (Mass)** | Gold / Orange / Yellow | Viscous, slow, heavy particles |
| **Gravity** | White / Blue / Purple | Structural, low-volatility |
| **Dark Energy** | Deep Purple / Violet / Magenta | Mysterious, expansive |
| **Neutrino** | Green / Cyan / Aqua | Fast, high-turbulence, ethereal |

---

## 🎮 Controls

### Audio Control Bar
After loading audio, a control bar appears with:
- **▶ Play / ⏸ Pause** - Toggle playback (or press `Spacebar`)
- **Progress Bar** - Click anywhere to seek
- **Time Display** - Shows current / total duration
- **New Track** - Load a different audio file
- **🎤 Mic** - Switch to microphone input

### Mouse Interaction
| Action | Effect |
|--------|--------|
| **Move** | Push particles, create ripples |
| **Drag** | Rotate camera orbit |
| **Scroll** | Zoom in/out |

### Keyboard Shortcuts
| Key | Action |
|-----|--------|
| `Space` | Play/Pause audio |
| `+` / `=` | Zoom in |
| `-` / `_` | Zoom out |
| `0` | Reset zoom to default |

### GUI Panel

#### Physics Engine
- **Field Type** - Switch between quantum field simulations
- **Density** - Particle count (0 - 275k)
- **Vortex Strength** - Rotational force intensity
- **Pulse Intensity** - Beat reaction strength

#### Bass Gate
- **Enable Gate** - Toggle the noise gate
- **Threshold** - Signal level to open gate (right = more sensitive)
- **Attack** - How quickly gate opens (0.01 - 0.3s)
- **Release** - How quickly gate closes (0.05 - 0.5s)
- **Ratio** - Compression amount above threshold

#### Optics & Visuals
- **Trail Persistence** - Afterimage decay rate
- **Bloom Strength** - Glow intensity
- **Anamorphic Flare** - Horizontal streak intensity
- **Chromatic Aberration** - Color fringing amount
- **Film Grain** - Noise texture intensity
- **Camera Shake** - Beat-reactive shake amount
- **Time Flow** - Simulation speed multiplier

---

## 🛠️ Technology Stack

| Technology | Purpose |
|------------|---------|
| **[Three.js](https://threejs.org/)** | 3D Rendering Engine |
| **GLSL** | Custom Vertex & Fragment Shaders |
| **Web Audio API** | FFT Analysis & Playback Control |
| **[Lil-GUI](https://lil-gui.georgealways.com/)** | Parameter Interface |

### Post-Processing Pipeline
1. Render Pass → 2. Afterimage (Trails) → 3. Unreal Bloom → 4. Anamorphic Flare → 5. Chromatic Aberration → 6. Film Grain → 7. Output

---

## 📊 Performance

| Setting | Particles | Target FPS |
|---------|-----------|------------|
| Low | ~50k | 60 fps |
| Medium | ~150k | 60 fps |
| High | ~275k | 30-60 fps |

Performance varies by GPU. Adjust **Density** slider for optimal framerate.

---

## 🧪 The Science Behind The Art

While this is an artistic interpretation, it is grounded in QFT concepts:

- **Vacuum Fluctuations:** The "noise" in the field represents the zero-point energy where virtual particles pop in and out of existence.
- **Excitations:** In QFT, a particle is not a solid sphere, but an excitation (vibration) in a field. When the bass kicks, the simulation increases the amplitude of these excitations, visualized as brighter, larger points.
- **Field Interactions:** Different field types exhibit different coupling strengths and behaviors, reflected in the varied turbulence and color patterns.

---

## 📝 Changelog

### v4.5 - Audio Control Edition
- Added play/pause functionality with spacebar shortcut
- Added progress bar with seek-to-click
- Added persistent audio control bar
- Added ability to load new tracks without refresh
- Added time display (current / duration)

### v4.25 - Bass Gate Edition
- Implemented professional bass gate with calibration
- Restored and enhanced zoom controls
- Added anamorphic lens flare effect
- Added secondary particle layer (25k particles)
- Added Neutrino field type
- Improved vortex system with dual rotation

### v4.1 - Enhanced Edition
- Upgraded to 7-band frequency analysis
- Implemented beat detection with onset detection
- Added spectral flux and centroid tracking
- Added chromatic aberration (beat-reactive)
- Added film grain post-processing
- Added camera shake on beats
- Increased particle count to 220k

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

*Created by [Theo B Harvey]*
