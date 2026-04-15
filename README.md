# 🎮 Wayne's Pixel Portfolio — Interactive 2D Resume

[繁體中文版](./README.zh-TW.md) | **English Version**

> **An interactive 2D pixel-art portfolio built with Phaser 3.**
> Navigate through a virtual isometric library as a capybara and explore my professional journey — including projects, skills, and academic milestones.

🔗 **Live Demo**: [https://waynepixelportfolio.vercel.app/](https://waynepixelportfolio.vercel.app/)

---

## ✨ Features

- **Explorable Pixel World** — Navigate an isometric library map featuring 8 interactive zones. Each room represents a core section of my resume: Profile, Projects, Skills, Achievements, Education & Experience, Certifications, Contact, and a cozy Break Room.
- **Bitmap Mask Pathfinding** — Implements a high-precision navigation system where walkable areas are defined by a pixel-level bitmap mask. Powered by an **A* grid search** algorithm with **flood-fill reachability validation**, ensuring the character intelligently avoids obstacles.
- **Animated Capybara Character** — Features a custom pixel-art capybara with diverse animation states: Walking, Standing (Front/Back), Working, Reading, Brainstorming, Drinking Coffee, and Resting.
- **Depth-Sorted Rendering** — Utilizes a layered depth system (Floor → Actor → Foreground Occluders) so the character naturally walks behind furniture and objects.
- **Bilingual Support** — Seamless, single-click toggle between English and Traditional Chinese for all UI panels.
- **Responsive Scaling** — Leveraging Phaser's `Scale.FIT` to adapt to any screen size while maintaining the 16:9 aspect ratio.

---

## 🛠 Tech Stack

| Layer | Technology |
| :--- | :--- |
| **Game Engine** | [Phaser 3.80](https://phaser.io/) |
| **Pathfinding** | A* Grid Search + Bitmap Walkable Mask |
| **Art Assets** | Derived from [ClawLibrary](https://github.com/) |
| **Typography** | VT323 (Google Fonts) |
| **Deployment** | [Vercel](https://vercel.com/) |

---

## 🎯 Technical Deep Dive: How It Works

1. **Pathfinding Logic**: A 2752×1536 reference mask defines traversable areas via red pixel values (`r > 180`). At runtime, the engine samples this mask to generate a 160×90 navigation grid for the **A* algorithm**.
2. **Connectivity Validation**: A **flood-fill algorithm** initiates from the spawn point to identify and retain only the connected walkable region, preventing "teleportation" glitches to isolated map areas.
3. **Route Optimization**: Once the A* algorithm finds a raw path, **collinear node removal** and **line-of-sight culling** are applied to smooth the trajectory for more natural movement.
4. **Interactive Orchestration**: Eight target nodes are strategically placed. Clicking a menu trigger dispatches the capybara to the corresponding coordinates before triggering the content modal.

---

## 📂 Project Structure

```bash
PixelPortfolio/
├── index.html
├── README.md
└── assets/
    ├── scene-floor.png 
    ├── scene-objects.png
    ├── walkable-mask.png
    └── actors/
        ├── walk-spritesheet.png
        ├── stand_front-spritesheet.png
        ├── stand_back-spritesheet.png
        ├── work-spritesheet.png
        ├── read-spritesheet.png
        ├── idea-spritesheet.png
        ├── coffee-spritesheet.png
        └── rest-spritesheet.png
---

## 📄 License / 授權

This is a personal portfolio project. All rights reserved.
Art assets are derived from [ClawLibrary](https://github.com/shengyu-meng/ClawLibrary) and are used under its original license terms.

---

<p align="center">
<i>Built with ☕ and pixels by Wayne Chou</i>
</p>
