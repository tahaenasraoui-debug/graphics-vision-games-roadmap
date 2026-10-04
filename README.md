# Graphics, Vision & Game Development Roadmap

 ![License](https://img.shields.io/badge/license-MIT-green.svg) ![language](https://img.shields.io/badge/language-C%2B%2B%20%7C%20python-blue.svg) ![focus](https://img.shields.io/badge/focus-rendering%20%2B%20vision%20%2B%20games-green.svg)

Three connected fields that share linear algebra and GPUs: render images, make machines see them, and turn both into interactive games.

## Table of Contents

1. [Workflow Overview](#workflow-overview)
2. [Prerequisites](#prerequisites)
3. [Phase 1: Rendering from Scratch](#phase-1-rendering-from-scratch)
4. [Phase 2: The GPU Pipeline](#phase-2-the-gpu-pipeline)
5. [Phase 3: Classical Computer Vision](#phase-3-classical-computer-vision)
6. [Phase 4: Deep Vision](#phase-4-deep-vision)
7. [Phase 5: Game Development](#phase-5-game-development)
8. [Capstone Projects](#capstone-projects)
9. [Repository Layout](#repository-layout)
10. [Engineering Rules](#engineering-rules)
11. [Exit Criteria](#exit-criteria)

---

## Workflow Overview

```
 Software rendering --> GPU pipeline --> Physically based rendering
        |                                         |
        v                                         v
 Classical vision --> Deep vision ----------> Game engine + capstone
 (OpenCV)             (CNNs, detection)       (Godot, game loop, physics)
```

## Prerequisites

- [ ] Linear algebra: vectors, matrices, transformations (Stage 0 and 3 of the ML roadmap)
- [ ] Programming in C++ or Python
- [ ] Basic calculus for lighting and optics

## Phase 1: Rendering from Scratch

Goal: Draw 3D scenes with nothing but arithmetic.

| Resource | Type | Why |
|----------|------|-----|
| [Computer Graphics from Scratch](https://gabrielgambetta.com/computer-graphics-from-scratch/) | Free book | Ray tracing and rasterization step by step |
| [Ray Tracing in One Weekend](https://raytracing.github.io/) | Free book series | Fast path to a working path tracer |
| [Scratchapixel](https://www.scratchapixel.com/) | Tutorials | Math and theory behind rendering |

- [ ] Write a software ray tracer: spheres, shadows, reflections
- [ ] Add materials, anti-aliasing, and a BVH
- [ ] Write a software rasterizer with a depth buffer

**Deliverables**
- [ ] `src/render/raytracer/` outputting PNGs
- [ ] Tests that compare small renders to reference images

## Phase 2: The GPU Pipeline

Goal: Use the GPU and write shaders.

| Resource | Type | Why |
|----------|------|-----|
| [LearnOpenGL](https://learnopengl.com/) | Free book | Modern OpenGL end to end |
| [The Book of Shaders](https://thebookofshaders.com/) | Free book | Fragment shader intuition |
| [WebGPU Fundamentals](https://webgpufundamentals.org/) | Tutorials | Modern graphics API in the browser |
| [Physically Based Rendering](https://pbr-book.org/) | Free book | Reference for lighting models |
| [Real-Time Rendering](http://www.realtimerendering.com/) | Resource site | Reference for real-time techniques |

- [ ] LearnOpenGL: getting started and lighting sections
- [ ] Implement Phong, then a PBR shader
- [ ] Shadow mapping and a post-processing effect

**Deliverables**
- [ ] `src/render/gpu/` OpenGL or WebGPU renderer loading a model with lighting
- [ ] Shader gallery in `docs/shaders.md`

## Phase 3: Classical Computer Vision

Goal: Understand image formation and geometry before neural networks.

| Resource | Type | Why |
|----------|------|-----|
| [OpenCV Tutorials](https://docs.opencv.org/4.x/d9/df8/tutorial_root.html) | Docs | Hands-on image processing |
| [Computer Vision: Algorithms and Applications](https://szeliski.org/Book/) | Free book | Reference text, read selectively |

- [ ] Filtering, edges, and feature detection
- [ ] Camera model and calibration
- [ ] Feature matching and homography: stitch a panorama
- [ ] Stereo or structure from motion basics

**Deliverables**
- [ ] `src/vision/classical/` panorama stitcher and camera calibration
- [ ] `notebooks/vision/` with results

## Phase 4: Deep Vision

Goal: Train and deploy models that classify, detect, and segment.

| Resource | Type | Why |
|----------|------|-----|
| [CS231n Course Notes](https://cs231n.github.io/) | Notes | Concise CNN theory, skip the lecture videos |
| [TorchVision](https://pytorch.org/vision/stable/index.html) | Docs | Pretrained models and datasets |
| [Ultralytics YOLO Docs](https://docs.ultralytics.com/) | Docs | Practical object detection |

- [ ] Train a CNN classifier on a real dataset and report error analysis
- [ ] Fine-tune a detector on a custom dataset you label
- [ ] Export a model and run it on video or a webcam

**Deliverables**
- [ ] `src/vision/deep/` with training and inference scripts, typed and tested
- [ ] `docs/error_analysis.md`

## Phase 5: Game Development

Goal: Ship small games with solid architecture.

| Resource | Type | Why |
|----------|------|-----|
| [Godot Documentation](https://docs.godotengine.org/en/stable/) | Docs | Open-source engine, strong 2D and 3D |
| [Game Programming Patterns](https://gameprogrammingpatterns.com/) | Free book | Architecture for game code |
| [Fix Your Timestep](https://gafferongames.com/post/fix_your_timestep/) | Article | Stable game loops and physics |
| [Red Blob Games](https://www.redblobgames.com/) | Tutorials | Pathfinding, grids, procedural generation |
| [The Nature of Code](https://natureofcode.com/) | Free book | Motion, forces, and simulation |
| [itch.io Game Jams](https://itch.io/jams) | Events | Deadlines force you to finish games |

- [ ] Build a complete 2D game: movement, collisions, scoring, menus
- [ ] Implement A* pathfinding and a simple AI state machine
- [ ] Enter one game jam and finish within the deadline

**Deliverables**
- [ ] `games/` with 2 finished games and playable builds
- [ ] Postmortem for each in `docs/postmortems/`

## Capstone Projects

- [ ] Renderer: a path tracer or real-time PBR renderer with a written technical breakdown
- [ ] Vision: a custom-trained detector running in real time on a webcam
- [ ] Game: a polished small game, optionally combining a vision input or procedural content
- [ ] Portfolio page with images and videos of each result

## Repository Layout

```
graphics-vision-games/
├── README.md
├── CMakeLists.txt
├── pyproject.toml
├── src/
│   ├── render/
│   │   ├── raytracer/
│   │   └── gpu/
│   └── vision/
│       ├── classical/
│       └── deep/
├── games/
├── assets/                   # small assets only; link large ones
├── notebooks/
├── tests/
└── docs/
    ├── shaders.md
    ├── error_analysis.md
    └── postmortems/
```

## Engineering Rules

These are strict. A phase is not complete until its deliverables follow all of them.

### 1. Daily 1:3 Theory-to-Building Ratio

- [ ] For every 1 hour of reading or watching, spend 3 hours building, solving, or running labs
- [ ] Log hours in `docs/log.md` at the end of each session
- [ ] No new chapter until the previous one has working code or a written lab report

### 2. Git Branch Hygiene

- [ ] `main` is always green and never receives direct commits
- [ ] One branch per deliverable: `phase-N/short-description`
- [ ] Small commits with imperative messages; squash-merge via PR after checks pass
- [ ] Delete branches after merge

### 3. Quality Gates

- [ ] C++: `clang-format`, `clang-tidy`, CMake, and [GoogleTest](https://google.github.io/googletest/) pass
- [ ] Python: `mypy --strict`, `ruff`, and `pytest` pass
- [ ] Image-output tests compare against reference renders with a stated tolerance
- [ ] Profile before optimizing and commit the profile numbers

### 4. Branch-Specific Rules

- [ ] Every result in the docs has an image or a number, not just a description
- [ ] Respect asset licenses: use CC0 or your own assets and credit sources
- [ ] Label and split datasets properly; never evaluate on training data
- [ ] Frame time budget: state a target (for example 16 ms) and measure against it

## Exit Criteria

- [ ] Render a lit 3D scene with shadows using code you wrote
- [ ] Explain the camera model and how a pixel maps to a ray
- [ ] Train a detector on your own dataset and analyze its failures
- [ ] Ship a finished game to a public page

