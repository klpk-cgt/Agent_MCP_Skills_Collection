---
name: algorithmic-art
description: "Creating algorithmic art using p5.js with seeded randomness and interactive parameter exploration. Use when users request creating art using code, generative art, algorithmic art, flow fields, or particle systems. Create original algorithmic art rather than copying existing artists' work to avoid copyright violations."
description_zh: "算法艺术：使用 p5.js 创建生成艺术（粒子系统、流场、递归结构），支持种子随机和交互参数探索"
version: 1.0.0
---

# Algorithmic Art

Algorithmic philosophies are computational aesthetic movements that are then expressed through code. Output .md files (philosophy), .html files (interactive viewer), and .js files (generative algorithms).

This happens in two steps:
1. Algorithmic Philosophy Creation (.md file)
2. Express by creating p5.js generative art (.html + .js files)

## ALGORITHMIC PHILOSOPHY CREATION

Create an ALGORITHMIC PHILOSOPHY (not static images or templates) that will be interpreted through:
- Computational processes, emergent behavior, mathematical beauty
- Seeded randomness, noise fields, organic systems
- Particles, flows, fields, forces
- Parametric variation and controlled chaos

**Name the movement** (1-2 words): "Organic Turbulence" / "Quantum Harmonics" / "Emergent Stillness"

**Articulate the philosophy** (4-6 paragraphs) covering:
- Computational processes and mathematical relationships
- Noise functions and randomness patterns
- Particle behaviors and field dynamics
- Temporal evolution and system states

### PHILOSOPHY EXAMPLES

**"Organic Turbulence"** - Chaos constrained by natural law. Flow fields driven by layered Perlin noise. Thousands of particles following vector forces.

**"Quantum Harmonics"** - Discrete entities exhibiting wave-like interference patterns. Particles with phase values that evolve through sine waves.

**"Recursive Whispers"** - Self-similarity across scales, infinite depth in finite space. Branching structures that subdivide recursively.

**"Field Dynamics"** - Invisible forces made visible through their effects on matter. Vector fields from mathematical functions or noise.

**"Stochastic Crystallization"** - Random processes crystallizing into ordered structures. Randomized circle packing or Voronoi tessellation.

## P5.JS IMPLEMENTATION

### Seeded Randomness (Art Blocks Pattern)

```javascript
let seed = 12345;
randomSeed(seed);
noiseSeed(seed);
```

### Parameter Structure

```javascript
let params = {
  seed: 12345,
  // colors, quantities, scales, probabilities, ratios, angles, thresholds
};
```

### Canvas Setup

```javascript
function setup() {
  createCanvas(1200, 1200);
}

function draw() {
  // Your generative algorithm
}
```

## INTERACTIVE ARTIFACT CREATION

Single self-contained HTML with:
- p5.js from CDN
- Seed navigation (prev/next/random/jump)
- Parameter controls (sliders, color pickers)
- Download PNG button

**CRITICAL**: This is a single artifact. No external files, no imports (except p5.js CDN). Everything inline.

## CRAFTSMANSHIP REQUIREMENTS

- **Balance**: Complexity without visual noise, order without rigidity
- **Color Harmony**: Thoughtful palettes, not random RGB values
- **Composition**: Even in randomness, maintain visual hierarchy and flow
- **Performance**: Smooth execution, optimized for real-time if animated
- **Reproducibility**: Same seed ALWAYS produces identical output
