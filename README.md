# Bloch Sphere Visualizer

An interactive 3D visualization tool for understanding single-qubit quantum states. Built with Three.js, this browser-based application lets you explore the Bloch sphere representation of quantum states through intuitive controls and animated quantum gate operations.

![Bloch Sphere](https://img.shields.io/badge/Quantum-Visualization-blue)
![Three.js](https://img.shields.io/badge/Three.js-r128-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

## Overview

The Bloch sphere is a geometrical representation of the pure state space of a two-level quantum mechanical system (qubit). Any pure qubit state can be represented as a point on the surface of this unit sphere, making it an invaluable tool for visualizing quantum operations and understanding quantum mechanics.

## Features

- **Interactive 3D Visualization** — Rotate, zoom, and explore the Bloch sphere from any angle
- **Dual Input Modes** — Define states using either spherical coordinates (θ, φ) or complex amplitudes (α, β)
- **Real-time Updates** — Watch the state vector move as you adjust parameters
- **Quantum Gate Animations** — Visualize X, Y, Z, and Hadamard gates as smooth rotations with trajectory trails
- **Preset States** — Quick access to common basis states |0⟩, |1⟩, |+⟩, |−⟩
- **Colorblind-Friendly** — Uses IBM's accessible color palette for clear visibility
- **Fully Client-Side** — No server required; runs entirely in your browser

## Getting Started

Simply open `index.html` in any modern web browser. No installation or build process required.

```bash
# Option 1: Open directly
open index.html

# Option 2: Serve locally (optional)
python -m http.server 8000
# Then visit http://localhost:8000/index.html
```

## Mathematical Background

### The Bloch Sphere Representation

Any pure single-qubit state can be written as:

```
|ψ⟩ = cos(θ/2)|0⟩ + e^(iφ) sin(θ/2)|1⟩
```

Where:
- **θ ∈ [0, π]** — Polar angle from the +Z axis
- **φ ∈ [0, 2π]** — Azimuthal angle in the X-Y plane

### Bloch Vector Coordinates

The state maps to a 3D unit vector (x, y, z) via:

| Coordinate | Formula | Description |
|------------|---------|-------------|
| x | sin(θ)cos(φ) | Projection onto X axis |
| y | sin(θ)sin(φ) | Projection onto Y axis |
| z | cos(θ) | Projection onto Z axis |

### Special States on the Sphere

| State | θ | φ | Bloch Vector | Location |
|-------|---|---|--------------|----------|
| \|0⟩ | 0 | — | (0, 0, 1) | North pole |
| \|1⟩ | π | — | (0, 0, −1) | South pole |
| \|+⟩ | π/2 | 0 | (1, 0, 0) | +X axis |
| \|−⟩ | π/2 | π | (−1, 0, 0) | −X axis |
| \|i⟩ | π/2 | π/2 | (0, 1, 0) | +Y axis |
| \|−i⟩ | π/2 | 3π/2 | (0, −1, 0) | −Y axis |

### Complex Amplitude Form

Alternatively, states can be expressed as:

```
|ψ⟩ = α|0⟩ + β|1⟩
```

Where α and β are complex numbers satisfying |α|² + |β|² = 1. The visualizer automatically normalizes any input amplitudes.

The conversion from amplitudes to angles:
- **θ = 2 arccos(|α|)**
- **φ = arg(β) − arg(α)**

## Quantum Gates

The visualizer animates four fundamental single-qubit gates:

### Pauli-X Gate (Bit Flip)
- **Matrix:** `[[0,1],[1,0]]`
- **Action:** π rotation around the X axis
- **Effect:** |0⟩ ↔ |1⟩

### Pauli-Y Gate
- **Matrix:** `[[0,-i],[i,0]]`
- **Action:** π rotation around the Y axis
- **Effect:** |0⟩ → i|1⟩, |1⟩ → -i|0⟩

### Pauli-Z Gate (Phase Flip)
- **Matrix:** `[[1,0],[0,-1]]`
- **Action:** π rotation around the Z axis
- **Effect:** |+⟩ ↔ |−⟩

### Hadamard Gate (H)
- **Matrix:** `1/√2 [[1,1],[1,-1]]`
- **Action:** Maps computational basis to superposition basis
- **Effect:** |0⟩ → |+⟩, |1⟩ → |−⟩

## Controls

### Mouse / Trackpad
| Action | Control |
|--------|---------|
| Rotate view | Click and drag |
| Zoom | Scroll wheel |

### Touch (Mobile/Tablet)
| Action | Control |
|--------|---------|
| Rotate view | Single finger drag |

### Interface Controls
| Control | Function |
|---------|----------|
| θ slider | Adjust polar angle (0 to π) |
| φ slider | Adjust azimuthal angle (0 to 2π) |
| α inputs | Set complex amplitude for \|0⟩ |
| β inputs | Set complex amplitude for \|1⟩ |
| Gate buttons | Apply quantum gate with animation |
| Preset buttons | Jump to common basis states |

## Color Scheme

The visualizer uses a colorblind-friendly palette based on IBM's design guidelines:

| Element | Color | Hex |
|---------|-------|-----|
| X Axis | Magenta | `#DC267F` |
| Y Axis | Gold | `#FFB000` |
| Z Axis | Blue | `#648FFF` |
| State Vector | Orange | `#FE6100` |
| \|0⟩ Label | Blue | `#648FFF` |
| \|1⟩ Label | Magenta | `#DC267F` |

## Technical Details

### Dependencies
- **Three.js r128** — 3D rendering (loaded via CDN)
- **Google Fonts** — JetBrains Mono typeface

### Browser Compatibility
- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

### File Structure
```
index.html    # Self-contained visualizer (HTML + CSS + JS)
README.md           # This documentation
```

## Educational Use

This visualizer is designed for:

- **Quantum computing courses** — Demonstrate qubit states and gate operations
- **Self-study** — Build intuition for quantum mechanics
- **Presentations** — Show quantum concepts interactively
- **Research** — Quick visualization of single-qubit states

## Understanding the Visualization

1. **The Sphere** — Represents all possible pure states of a qubit
2. **The Orange Arrow** — Shows the current quantum state
3. **North Pole (|0⟩)** — The computational basis state "zero"
4. **South Pole (|1⟩)** — The computational basis state "one"
5. **Equator** — Equal superposition states (|+⟩, |−⟩, |i⟩, |−i⟩)
6. **Trail Lines** — Show the path during gate animations

## Examples

### Creating a Superposition
1. Start at |0⟩ (click the |0⟩ preset button)
2. Click the **H** (Hadamard) gate button
3. Watch the state rotate to |+⟩ on the equator

### Exploring Phase
1. Set θ = π/2 (equator)
2. Slide φ from 0 to 2π
3. Observe the state vector rotating around the equator

### Bit Flip Operation
1. Start at |0⟩
2. Click the **X** gate button
3. Watch the state flip to |1⟩ (south pole)

## License

MIT License — Feel free to use, modify, and distribute for educational and commercial purposes.

## Acknowledgments

- Bloch sphere concept by Felix Bloch (1946)
- Color palette based on IBM's colorblind-safe design guidelines
- Built with Three.js by mrdoob and contributors
