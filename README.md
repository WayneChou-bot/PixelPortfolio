# 🎮 Wayne's Pixel Portfolio — 2D 像素風履歷網站

> **An interactive 2D pixel-art portfolio built with Phaser 3.**
> Walk through a virtual library as a capybara and explore my career — projects, skills, achievements, and more.
>
> **以 Phaser 3 打造的 2D 像素風互動式履歷。**
> 操控水豚角色在虛擬圖書館中漫步，探索我的職涯經歷。

<!-- 🔗 Live Demo: https://your-domain.vercel.app -->
<!-- 部署完成後請取消上方註解並填入網址 -->

---

## ✨ Features / 功能特色

**Explorable Pixel World 像素世界探索** — Navigate an isometric library map with 8 interactive rooms, each representing a section of my resume: Profile（個人簡介）, Projects（專案展示）, Skills（技能圖鑑）, Achievements（成就展示）, Education & Experience（學經歷總覽）, Certifications（證照文件）, Contact（聯繫方式）, and a cozy Break Room（休息室）.

**Bitmap Mask Pathfinding 點陣遮罩尋路** — Walkable areas are defined by a pixel-level bitmap mask (red = walkable), powering an A\* grid search with flood-fill reachability validation. The character intelligently navigates narrow corridors and avoids obstacles.

**Animated Capybara Character 水豚動畫角色** — A custom pixel-art capybara with multiple animation states: walking, standing (front/back), working, reading, having ideas, drinking coffee, and resting.

**Depth-Sorted Rendering 深度排序渲染** — Implements a layered depth system (floor → actor → foreground occluder) so the character naturally walks behind furniture and objects, matching the original ClawLibrary engine behavior.

**Bilingual Content 雙語內容** — All panels support English/Chinese toggle（中英切換）with a single click.

**Responsive Scaling 響應式縮放** — Uses Phaser's `Scale.FIT` + `CENTER_BOTH` to adapt to any screen size while maintaining the 16:9 aspect ratio.

---

## 🛠 Tech Stack / 技術架構

| Layer | Technology |
|-------|-----------|
| Game Engine 遊戲引擎 | [Phaser 3.80](https://phaser.io/) |
| Pathfinding 尋路演算法 | A\* grid search + bitmap walkable mask |
| Art Assets 美術素材 | [ClawLibrary](https://github.com/) pixel tileset |
| Icons 圖示 | [Font Awesome 6.5](https://fontawesome.com/) |
| Font 字型 | VT323 (Google Fonts) |
| Deployment 部署 | Single HTML — ready for Vercel / GitHub Pages |

---

## 📂 Project Structure / 專案結構

```
2D像素版/
├── index.html                  # Single-file app（單檔應用）
├── README.md
└── assets/
    ├── scene-floor.png         # Floor layer（地板圖層）
    ├── scene-objects.png       # Foreground objects（前景物件）
    ├── walkable-mask.png       # Bitmap walkable mask（可行走遮罩）
    └── actors/
        ├── walk-spritesheet.png
        ├── stand_front-spritesheet.png
        ├── stand_back-spritesheet.png
        ├── work-spritesheet.png
        ├── read-spritesheet.png
        ├── idea-spritesheet.png
        ├── coffee-spritesheet.png
        └── rest-spritesheet.png
```

---

## 🚀 Getting Started / 快速開始

### Local Development 本機開發

Any static file server will work. For example:

```bash
# Using Python
cd 2D像素版
python -m http.server 8000

# Using Node.js
npx serve .
```

Then open `http://localhost:8000` in your browser.

### Deploy to Vercel 部署到 Vercel

1. Push this folder to a GitHub repository.
2. Import the repo on [vercel.com](https://vercel.com).
3. Set the **Root Directory** to `2D像素版`.
4. Deploy — no build step needed（無需建置步驟）.

---

## 🎯 How It Works / 運作原理

1. **Bitmap Mask** — A 2752×1536 reference image defines walkable areas with red pixels (`r > 180, g < 120, b < 120`). At runtime the mask is sampled to build a 160×90 A\* grid.
2. **Flood Fill** — Starting from the spawn point, only the connected walkable region is kept, preventing the character from teleporting to isolated patches.
3. **Path Simplification** — After A\* finds a path, collinear nodes are removed and line-of-sight culling smooths the route.
4. **Interactive Nodes** — Eight walk nodes are placed in walkable zones. Clicking a menu item sends the capybara walking to the corresponding room, then opens a content panel.

---

## 📸 Screenshots / 截圖

<!-- 部署後可加入截圖 -->
<!-- Add screenshots after deployment -->

*Coming soon — 即將新增*

---

## 📄 License / 授權

This is a personal portfolio project. All rights reserved.
Art assets are derived from [ClawLibrary](https://github.com/) and are used under its original license terms.

本專案為個人作品集，保留所有權利。美術素材源自 ClawLibrary，依其原始授權條款使用。

---

<p align="center">
  <i>Built with ☕ and pixels by Wayne</i>
</p>
