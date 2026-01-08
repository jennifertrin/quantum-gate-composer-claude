# Quantum Circuit Composer

A browser-based quantum computing circuit composer for visually designing, editing, and simulating quantum circuits. Built as an educational tool to help learn quantum computing concepts through hands-on experimentation.

## Features

**Circuit Editor**
- Drag-and-drop gate placement onto a grid-based circuit
- Support for 1-10 qubits with add/remove controls
- Repositioning of existing gates by dragging
- Two-step placement for multi-qubit gates with visual feedback
- Zoom controls (50%-200%) for navigating large circuits
- Step-by-step execution mode

**Available Gates**
- Single-qubit: H, X, Y, Z, S, T, Rx, Ry, Rz
- Multi-qubit: CNOT, CZ, SWAP
- Measurement

**Simulation & Visualization**
- Full state vector simulation
- Probability histogram
- 3D Bloch sphere visualization (Three.js)
- Complex amplitude display

**Import/Export**
- JSON format for saving and loading circuits
- OpenQASM 2.0 export for use with other quantum platforms

**Preset Examples**
- Bell State
- GHZ State
- Equal Superposition
- Quantum Teleportation
- Phase Kickback

## Usage

Open `index.html` in any modern browser. Drag gates from the left palette onto the circuit grid, then click "Run" to simulate.

**Multi-qubit gates:** Drop on the first qubit, then click on the second qubit to complete placement. Press Escape to cancel.

**Keyboard Shortcuts**
- `Delete` / `Backspace` - Delete selected gate
- `Escape` - Deselect or cancel placement
- `Ctrl + R` - Run simulation

## Technical Details

Single HTML file with embedded React, Three.js, and Babel (loaded via CDN). No build process required.

- State vector representation with 2^n complex amplitudes
- Unitary matrix operations for all gates
- Bloch vectors calculated from reduced density matrices

## Browser Support

Chrome, Firefox, Safari, Edge

## License

MIT License
