<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=28&duration=3000&pause=1000&color=7C5CFF&center=true&vCenter=true&width=800&lines=Vairaj+Malhotra;Deep+Learning+%2B+Simulation+%2B+Developer+Tools;Learning+by+vibecoding%2C+one+commit+at+a+time" alt="Typing intro" />

<p>
  <img src="https://img.shields.io/badge/B.Tech-VIT%20Vellore-7C5CFF?style=for-the-badge" alt="B.Tech at VIT Vellore" />
  <img src="https://img.shields.io/badge/Focus-Full--Stack%20%2B%20ML-181717?style=for-the-badge" alt="Focus: Full-Stack and ML" />
  <img src="https://img.shields.io/badge/Status-Always%20Trying-2ea44f?style=for-the-badge" alt="Always trying" />
</p>

</div>

---

## 👋 About Me

I'm a B.Tech student at **VIT Vellore** exploring AI and ML. I enjoy full-stack development, and lately I've been digging into **deep learning for image restoration**, **agent-based simulation**, and **developer tooling built on static analysis**. I'm still firmly in the learning phase and figuring things out as I go.

My process is simple: **read the docs → break things → ask claude → fix them → repeat** until it works.

Right now I'm focused on:

- 🧠 Understanding *why* model architectures and loss functions work, not just how to run them
- 🧱 Writing cleaner backend logic and wiring it to functional React interfaces
- 🤝 Building with teams and learning from how others approach problems

---

## 🏆 SEMICON India Hackathon 2026: KLA Track

**The challenge:** restore degraded grayscale semiconductor (SEM/TEM) images by removing noise and upscaling 2× in a single pass. I built my own solution and also contributed to our team's (**Team GitWarriors, VIT Vellore**).

### 🔬 My Solution: NAFNet-Inspired Network · [Semicon-Hackathon-KLA-Solution-2](https://github.com/Fabastic/Semicon-Hackathon-KLA-Solution-2)

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![NAFNet](https://img.shields.io/badge/NAFNet--inspired-7C5CFF?style=flat-square)
![Computer Vision](https://img.shields.io/badge/Computer%20Vision-181717?style=flat-square)

A custom network designed to beat standard U-Net baselines on both structural accuracy and inference speed.

| What | How |
|---|---|
| ⚡ **Efficient blocks** | NAFBlocks with a SimpleGate instead of ReLU/GELU, plus Simplified Channel Attention |
| 🧩 **Clean upscaling** | PixelShuffle instead of interpolation or ConvTranspose, so no checkerboard artifacts |
| 🎯 **Sharp semiconductor lines** | Composite loss: **L1** (1.0) + **Sobel edge** (0.3) + **FFT** (0.1) |
| 🛡️ **Robust to unseen noise** | LayerNorm2d and on-the-fly speckle and Gaussian noise augmentation |
| 📏 **Measured properly** | SSIM and PSNR benchmarking on a validation set |

**What I took from it:** loss design matters as much as architecture. Adding edge and frequency-domain terms is what keeps a restoration model from blurring fine lines.

### 🤝 Team Solution: Lightweight U-Net · [Semicon-Hackathon-KLA-Solution](https://github.com/Fabastic/Semicon-Hackathon-KLA-Solution)

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Team Project](https://img.shields.io/badge/Team%20Project-7C5CFF?style=flat-square)

Our submitted solution: a U-Net that jointly denoises and upscales in one forward pass, handling both **128→256** and **256→512** image pairs, with trained weights and one-command inference.

<div align="center">

| 📈 SSIM | 📡 PSNR | 🧮 Parameters | ⚡ CPU inference | 🕑 Training |
|:---:|:---:|:---:|:---:|:---:|
| **0.6996** | **25.80 dB** | **~13.5M** | **~150 ms / image** | **~2 hrs** on a Colab T4 |

</div>

- **Loss:** L1 plus a Sobel edge term (`L = L1 + 0.3·L_edge`)
- **Upscaling:** PixelShuffle sub-pixel convolution with a global bilinear residual
- **Honest about limits:** the repo documents its own weaknesses, including 3,200 training samples, no perceptual loss, and limited out-of-distribution testing

---

## 🧠 ContextOS · [Fabastic/ContextOS](https://github.com/Fabastic/ContextOS)

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)

**A developer tool that statically analyzes a codebase and turns it into a queryable behavioral map**, linking source files, AST symbols, API routes, frontend components and user-facing capabilities. The idea: *deterministic analysis first, AI explanation last.*

**My role:** Frontend & UI contributor. I built the frontend workspace and the reference apps (GraviBank, GraviComm), and worked on the FastAPI environments that feed the analysis engine.

```
Source code (Python AST + TypeScript AST)
   → Cross-layer resolution (frontend calls ↔ backend routes)
   → Behavioral graph (NetworkX)  → PostgreSQL run history
   → File watcher + changeset diffing
   → Impact analysis (BFS + risk score)
   → Scenario tests → Regression evidence → Capability discovery
```

| Capability | What it does |
|---|---|
| 🔍 **Static analysis** | Parses Python (`ast`) and React/TypeScript (`ts-morph`) to extract routes, handlers, components and API calls |
| 🗺️ **Behavioral graph** | Maps business features like *Withdraw* and *Deposit* to the exact files and functions behind them |
| 👀 **Live watching** | Re-analyzes on file save and diffs runs using stable content hashes, with no fake node churn |
| 💥 **Impact analysis** | Breadth-first traversal from changed code to affected behaviors, with a risk score |
| ✅ **Regression evidence** | Runs scenario tests and links *code change → impact → failing test* in one chain |
| 🧩 **Capability discovery** | Detects new multi-layer features (a Loan feature across database, route and UI) from structure alone |
| 🎨 **Interactive visualizer** | React Flow dashboard with behavior path highlighting and source inspection |

Ships with **Banking** and **E-commerce** reference apps, automated test suites, and demo walkthroughs. The Banking graph alone has 76 nodes and 96 edges across 5 behaviors.

---

## 🌍 Civilization Systems (CivSys) · [code2create-CivSys](https://github.com/Fabastic/code2create-CivSys)

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Three.js](https://img.shields.io/badge/Three.js-000000?style=flat-square&logo=threedotjs&logoColor=white)
![Team Project](https://img.shields.io/badge/Team%20Brogrammers-7C5CFF?style=flat-square)

Built for **Code2Create 7.0** with **Team Brogrammers**. An artificial-civilization and agent-based simulation lab asking one question: **can economic collapse, mass migration or institutional welfare emerge from many simple, bounded-rational agents, without scripting any of it?**

**Why it's different:** many LLM-driven agent sims are slow, costly and impossible to reproduce. CivSys is a **pure-Python deterministic engine** with seeded randomness, so the same seed always gives the same history, and nothing needs a model call per tick.

| What | How |
|---|---|
| 🗺️ **Living world** | A 128×128 procedural map with biomes and fertility that agents actually extract from and change |
| 🧑 **Rich agents** | Needs, personality, emotions, perception, episodic memory, beliefs, skills, inventory, relationships and group membership |
| 🎲 **Bounded-rational decisions** | Utility scoring plus softmax selection from a seeded RNG (work, eat, migrate, cooperate) |
| 💰 **Dynamic economy** | Supply and demand markets with EMA pricing, production, and institutional wealth redistribution |
| 🧪 **Reproducible experiments** | Run Control and Treatment branches from the same seed, then inject an event like a **drought** into one |
| 🔎 **Causal ledger** | Trace *why* an agent migrated or died through recorded state transitions |
| 🎮 **2.5D visualization** | React Three Fiber renderer that only draws what the engine decided, kept separate from the simulation |

**The drought demo:** crop output falls, food gets scarce, prices climb, work stops paying off, and agents start migrating. Nobody told them to.

```
Simulation engine (Python) → FastAPI REST + WebSocket → React + Zustand → React Three Fiber (2.5D world)
```

**Stack:** Python • FastAPI • NumPy / SciPy • NetworkX • Pydantic • PostgreSQL • React 18 • TypeScript • Vite • Tailwind • Three.js • Zustand • React Flow • Recharts

This is the **Review 1** build. The repo documents what works today (world, agents, economy, groups, experiments, causal tracing, 2.5D view) and a Phase 3 roadmap (larger world, births and aging, deeper culture, full real-time streaming).

---

## 🛠️ Tech Stack

<div align="center">

| | |
|---|---|
| **Languages** | ![Python](https://img.shields.io/badge/Python-181717?style=for-the-badge&logo=python&logoColor=white&labelColor=0d1117) ![TypeScript](https://img.shields.io/badge/TypeScript-181717?style=for-the-badge&logo=typescript&logoColor=white&labelColor=0d1117) ![SQL](https://img.shields.io/badge/SQL-181717?style=for-the-badge&logo=postgresql&logoColor=white&labelColor=0d1117) ![HTML5](https://img.shields.io/badge/HTML5-181717?style=for-the-badge&logo=html5&logoColor=white&labelColor=0d1117) ![CSS3](https://img.shields.io/badge/CSS3-181717?style=for-the-badge&logo=css3&logoColor=white&labelColor=0d1117) |
| **ML / Vision** | U-Net • NAFNet-style blocks • PixelShuffle • Sobel & FFT losses • SSIM / PSNR |
| **Simulation** | Agent-based modelling • NumPy / SciPy • NetworkX • seeded, reproducible experiments |
| **Frontend** | ![React](https://img.shields.io/badge/React-181717?style=for-the-badge&logo=react&logoColor=white&labelColor=0d1117) ![Vite](https://img.shields.io/badge/Vite-181717?style=for-the-badge&logo=vite&logoColor=white&labelColor=0d1117) ![Tailwind](https://img.shields.io/badge/Tailwind-181717?style=for-the-badge&logo=tailwindcss&logoColor=white&labelColor=0d1117) ![Three.js](https://img.shields.io/badge/Three.js-181717?style=for-the-badge&logo=threedotjs&logoColor=white&labelColor=0d1117) |
| **Backend** | ![FastAPI](https://img.shields.io/badge/FastAPI-181717?style=for-the-badge&logo=fastapi&logoColor=white&labelColor=0d1117) |
| **Databases** | ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-181717?style=for-the-badge&logo=postgresql&logoColor=white&labelColor=0d1117) ![SQLite](https://img.shields.io/badge/SQLite-181717?style=for-the-badge&logo=sqlite&logoColor=white&labelColor=0d1117) |
| **Tools** | ![Git](https://img.shields.io/badge/Git-181717?style=for-the-badge&logo=git&logoColor=white&labelColor=0d1117) ![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white&labelColor=0d1117) |

</div>

---

## 📊 GitHub Stats

<div align="center">

<img height="170" src="https://github-readme-stats.vercel.app/api?username=Fabastic&show_icons=true&theme=tokyonight&hide_border=true" alt="GitHub stats" />
<img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Fabastic&layout=compact&theme=tokyonight&hide_border=true" alt="Top languages" />

<img src="https://github-readme-streak-stats.herokuapp.com/?user=Fabastic&theme=tokyonight&hide_border=true" alt="GitHub streak" />

</div>

---

## 🌱 Currently

- 🔭 Improving restoration models: better losses, more data, and proper out-of-distribution testing
- 🧪 Levelling up on **FastAPI** and **React + TypeScript**
- 🏆 Collecting achievements, starting with **Pull Shark** 🦈

---

## 🤝 Let's Connect

I'm always happy to talk code, swap project ideas, or collaborate on something new.

<div align="center">

[![GitHub](https://img.shields.io/badge/GitHub-Fabastic-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Fabastic)

*"Read the docs, make plenty of mistakes, keep iterating."* ✨

</div>
