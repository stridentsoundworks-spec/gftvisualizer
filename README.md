# ⚛️ Quantum Visuals: Audio-Reactive Quantum Field Simulator

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![WebGL](https://img.shields.io/badge/WebGL-Three.js-black)
![Status](https://img.shields.io/badge/status-Stable-green)

**A High-Definition, interactive 3D simulation of Quantum Field Theory (QFT) that reacts to audio analysis in real-time.**

This project visualizes the concept of vacuum fluctuations and particle excitations using GPU-accelerated fluid dynamics. 
It renders up to **200,000 interactive particles** in the browser using custom GLSL shaders, 
simulating the behavior of different quantum fields (Electromagnetic, Strong Force, Higgs, and Gravity).

Enable the bass gate to make the simulator pulse with your music. 
The threshold and audio sensitivity settings interact so may need a tweak based on the input material.
Gate Threshold slider to the right = pulse more likely to be triggered. 
Gate Threshold slider to the left = pulse less likely to be triggered. 

Disable bass gate for voice/mic input to reduce pulse effect.

I will update the readme further but I am tired and winding down for the day now. 
Enjoy the updates!! :D 

---

## 🚀 Live Demo
** DEMO 🔗 (https://qftvisualizer.netlify.app)**
*(Note: Microphone access is required for the live audio reactivity feature)*

---

## ✨ Key Features

### 🎨 High-Fidelity Visuals
*   **Volumetric Point Cloud:** Renders 180k+ particles efficiently using `THREE.Points`.
*   **Cinematic Post-Processing:** Features Optical Bloom, Depth of Field (DoF), Chromatic Aberration, and CRT Scanline overlays.
*   **Particle Trails:** Implements Afterimage processing for high-energy "bubble chamber" trail effects.

### 🔊 Audio Intelligence
*   **Real-Time FFT Analysis:** Deconstructs audio into Bass, Mids, and High frequencies.
*   **Dynamic Reactivity:**
    *   **Bass:** Triggers shockwave expansions and thermal brightening (collision flashes).
    *   **Mids:** Controls time dilation (simulation speed) and turbulence.
    *   **Highs:** Modulates particle sparkle and color separation.
*   **Input Modes:** Supports local MP3 file upload or live Microphone/System Audio input.

### ⚗️ Physics Engine
*   **Curl Noise Fluid Dynamics:** Simulates non-divergent fluid flow to mimic quantum vacuum fluctuations without heavy CPU cost.
*   **Interactive Collider:** The mouse cursor acts as a high-energy probe, physically displacing particles and creating vortices in the field.
*   **4 Field Presets:**
    1.  **Photon (EM):** Fluid, fast-moving, cyan/blue.
    2.  **Gluon (Strong):** Chaotic, high-turbulence, red/purple.
    3.  **Higgs (Mass):** Viscous, slow-moving, heavy gold/amber.
    4.  **Gravity:** Structural, low-volatility, monochromatic.  
    5.  **Dark Energy:**
    6.  **Neutrino**


---

## 🎮 Controls

### The HUD (Heads Up Display)
*   **Load Audio File:** Upload an MP3 to visualize a specific track.
*   **Initialize Sensors:** Activates the microphone for live visualization.

### Interaction
*   **Mouse Move:** Move your cursor through the cloud to push particles and create ripples.
*   **Mouse Drag:** Rotate the camera orbit.
*   **Scroll:** Zoom in/out of the quantum volume.

### Laboratory Panel (GUI)
*   **Audio Sensitivity:** Adjust gain to match your volume level.
*   **Field Type:** Switch between different particle physics models.
*   **Density:** Real-time control of particle count (0 - 200k).
*   **Visuals:** Adjust Trail Persistence, Bloom Strength, and Time Flow.

---

## 🛠️ Technology Stack

*   **[Three.js](https://threejs.org/):** 3D Rendering Engine.
*   **GLSL (OpenGL Shading Language):** Custom Vertex and Fragment shaders for high-performance particle physics.
*   **Web Audio API:** For Frequency Analysis (FFT).
*   **Lil-GUI:** Floating interface for parameter tuning.

---


---

## 🧪 The Science Behind The Art

While this is an artistic interpretation, it is grounded in QFT concepts:
*   **Vacuum Fluctuations:** The "noise" in the field represents the zero-point energy where virtual particles pop in and out of existence.
*   **Excitations:** In QFT, a particle is not a solid sphere, but an excitation (vibration) in a field. When the bass kicks, the simulation increases the amplitude of these excitations, visualized as brighter, larger points.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

*Created by [Theo B Harvey]*
