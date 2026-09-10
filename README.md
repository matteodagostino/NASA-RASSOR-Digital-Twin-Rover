# NASA RASSOR Digital Twin Rover

> **UCF Senior Design | Florida Space Institute-supported | Lunar robotics, digital twins, and simulation-gated autonomy**

A multidisciplinary senior design project centered on a **RASSOR-inspired four-wheel lunar rover testbed** and a **live, scene-aware digital twin** for safer remote and autonomous surface operations. The system connected physical rover hardware with RGB-D scene reconstruction, state estimation, NVIDIA Isaac Sim physics playback, and command validation before rover actuation.

## Project Highlights

- 🏆 **Finalist** — 2026 UCF Industrial Engineering & Management Systems Senior Design Showcase
- 🥇 **1st Place** — Senior Design Project Competition, 7th Latin American IEOM Conference, Panama City (2026)
- 🥇 **1st Place** — Poster Competition, 7th Latin American IEOM Conference, Panama City (2026)
- 📄 Project research later developed into conference/proceedings work with the senior design team listed as co-authors
- 🚀 Project supported by funding from the **Florida Space Institute**

## The Problem

Lunar surface operations introduce a fundamental control challenge: communication delay and intermittent connectivity make continuous Earth-based teleoperation difficult, while fully open-loop autonomy can be risky in partially observed terrain.

Our project investigated whether a synchronized digital twin could serve as a safety layer between a proposed rover command and the physical vehicle. Rather than immediately executing a candidate command sequence, the system could reconstruct the rover's surroundings, synchronize the virtual rover state, replay the command in physics, and evaluate whether it should be approved, held, or rejected.

## System Overview

The final research architecture combined:

- **Physical rover:** four-wheel, skid-steer RASSOR-inspired testbed
- **RGB-D sensing:** rover-mounted LiDAR-equipped smartphone
- **Scene reconstruction:** NVIDIA nvblox
- **State estimation:** NVIDIA cuVSLAM
- **Digital twin / physics:** NVIDIA Isaac Sim
- **Communication:** ROS 2
- **Command validation:** feasibility, collision, clearance, endpoint-position, and heading checks

```text
Candidate Command
       │
       ▼
Live Rover State + RGB-D Scene
       │
       ▼
Synchronized Digital Twin
(nvblox + cuVSLAM + Isaac Sim)
       │
       ▼
Physics Playback / Safety Checks
       │
   ┌───┴───────────┐
   ▼               ▼
APPROVE         HOLD / REJECT
   │
   ▼
Physical Rover via ROS 2
```

## My Contributions — Matteo D'Agostino

This was a collaborative senior design project. My primary role was **Assembly and Development**, alongside technical documentation and project support.

### Rover Assembly & Hardware Development

I worked directly on the physical rover platform, including:

- Manual assembly of the rover and its drivetrain components.
- Integration and setup of electrical components used by the rover platform.
- Hardware testing during development to determine why the rover was not operating as expected.
- Diagnosing mechanical assembly problems in the drive system.
- Disassembling and rebuilding rover components after identifying hardware issues.
- Supporting replacement/reprinted components and subsequent reassembly.
- Testing the rover after hardware changes to evaluate whether movement and stability improved.

This work required moving beyond the original assembly instructions and systematically determining whether failures were coming from mechanical fit, drivetrain assembly, electrical integration, or software/communication behavior.

### Technical Documentation & Research

I contributed directly to multiple project reports:

- **Project Proposal Report** — Section 2, *Problem Statement*, and Section 7, *Standards*.
- **AS-IS Report** — *Broader Impacts on Sustainability and Beyond*.
- **TO-BE Report** — *Sources of Knowledge, Standards, and Best Practices Consulted*.

My research included engineering and safety standards, responsible computing considerations, teleoperation literature, material/safety documentation, and the broader sustainability implications of digital-twin and autonomous robotic systems.

## From Physical Rover to Digital Twin

The project evolved through several stages:

1. **Define the problem** — understand the limitations of remotely operating a lunar rover under communication latency.
2. **Build the physical platform** — assemble the RASSOR-inspired rover, drivetrain, electronics, and sensing platform.
3. **Diagnose hardware behavior** — identify mechanical/electrical issues affecting reliable rover movement and rebuild components where necessary.
4. **Establish rover communication** — connect the physical platform to the software/control environment.
5. **Construct the digital twin** — synchronize rover state and reconstructed surroundings in simulation.
6. **Validate candidate commands** — replay proposed wheel-command sequences in physics before physical execution.
7. **Measure sim-to-real fidelity** — compare simulated endpoints with physical rover measurements and use discrepancies to improve calibration.

> The digital-twin architecture, command-validation research, and later experimental results described below were **team outcomes**. They are included to explain the system my hardware and assembly work supported, not as claims that I personally implemented every component.

## Experimental Results — Team Outcomes

The later research phase evaluated both the command-validation gate and agreement between the digital twin and physical rover.

### Simulation Gate

A controlled battery of **100 logical trials** evaluated clear and blocked direct paths and generated route candidates. Direct controls agreed with the analytical labels across all trials: **25/25 clear paths were approved and 75/75 blocked paths were rejected**.

Physics playback also exposed failures that a waypoint-level geometric screen did not. Of 55 withheld generated candidates, **34 stalled or became wedged only during simulated execution**.

### Sim-to-Real Calibration

Physical testing revealed a distance-dependent motor calibration bias. For the 1.00 m forward command, simulated-to-measured endpoint error was initially **7.9 cm**.

After recalibrating the rover's wheel-step parameters:

- 1.00 m forward error decreased from **7.9 cm → 0.7 cm**.
- Post-calibration endpoint/pivot errors ranged from **0.3–0.7 cm** across the tested conditions.
- Mean simulated-to-measured error across those conditions was approximately **0.5 cm**.

These results demonstrate how the team's digital twin could support both command screening and physical rover calibration.

## Recognition

### UCF Senior Design Showcase — 2026

The project was selected as a **finalist in the Industrial Engineering & Management Systems senior design competition** and presented at UCF's 2026 Senior Design Showcase.

### IEOM Latin American Conference — Panama City, 2026

The work was subsequently presented at the **7th Latin American Conference on Industrial Engineering and Operations Management**, held in Panama City, Panama, August 4–6, 2026.

The project received:

- **First Place — Senior Design Project Competition**
- **First Place — Poster Competition**

## Research Output

Work originating from the senior design project was later developed into conference/proceedings research. I am listed as a **co-author based on my contributions to the underlying senior design project and prior project work**; I did **not** personally write the later conference/proceedings manuscript.

This distinction is intentional: this repository focuses on the work I personally performed during senior design while acknowledging the subsequent research outcomes of the team.

## Project Showcase Video

▶️ **Project video:** https://www.youtube.com/watch?v=eT9YaH16bUE

## Technologies & Concepts

`ROS 2` · `NVIDIA Isaac Sim` · `NVIDIA nvblox` · `NVIDIA cuVSLAM` · `RGB-D / LiDAR` · `Digital Twins` · `Robotics` · `Simulation` · `3D Printing` · `Hardware Integration` · `Sim-to-Real Validation`

## Repository Roadmap

Project media and selected supporting artifacts will be organized here as they are prepared for public release:

```text
NASA-RASSOR-Digital-Twin-Rover/
├── README.md
├── assets/
│   ├── rover/
│   ├── hardware/
│   ├── showcase/
│   └── awards/
└── docs/
    └── publication-links.md
```

> **Attribution:** This repository documents my work and experience as a member of a multidisciplinary UCF senior design team. Results described as project or research outcomes reflect collaborative team work; sections labeled **My Contributions** describe my individual involvement.
