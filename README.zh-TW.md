# 🎮 Wayne 的像素作品集 — 2D 互動式履歷網站

**繁體中文版** | [English Version](./README.md)

> **以 Phaser 3 打造的 2D 像素風互動式履歷。**
> 操控水豚角色在虛擬圖書館中漫步，探索我的職涯經歷——包含專案、技能、成就與學歷。

🔗 **線上演示**: [https://waynepixelportfolio.vercel.app/](https://waynepixelportfolio.vercel.app/)

---

## ✨ 功能特色

- **像素世界探索** — 在包含 8 個互動區域的等角投影地圖中導航。每個房間代表履歷的不同區塊：個人簡介、專案展示、技能圖鑑、成就展示、學經歷、證照、聯繫方式以及休息室。
- **點陣遮罩尋路** — 實作高精度導航系統，透過像素級別的點陣遮罩定義可行走區域。結合 **A* 尋路演算法**與 **Flood-fill 連通性驗證**，確保角色能智慧避障。
- **水豚動畫角色** — 客製化水豚像素動畫，包含多種狀態：走路、站立（前後）、工作、閱讀、思考、喝咖啡以及休息。
- **深度排序渲染** — 採用分層深度系統（地板 → 角色 → 前景遮擋物），讓角色能自然地穿梭於家具與物件前後。
- **雙語切換** — 支援一鍵切換英文與繁體中文介面。
- **響應式縮放** — 利用 Phaser 的 `Scale.FIT` 模式，在保持 16:9 比例的同時適應各類螢幕尺寸。

---

## 🛠 技術架構

| 層級 | 使用技術 |
| :--- | :--- |
| **遊戲引擎** | [Phaser 3.80](https://phaser.io/) |
| **尋路演算法** | A* Grid Search + Bitmap Walkable Mask |
| **美術素材** | 源自 [ClawLibrary](https://github.com/shengyu-meng/ClawLibrary) |
| **字型** | VT323 (Google Fonts) |
| **部署平台** | [Vercel](https://vercel.com/) |

---

## 🎯 核心技術原理：深入探討

1. **尋路邏輯**：透過解析 2752×1536 的參考遮罩，利用紅色彩道（`r > 180`）定義可行走區域。引擎在執行時會採樣此遮罩，產生一個 160×90 的網格供 **A* 演算法**使用。
2. **連通性驗證**：透過 **Flood-fill 演算法** 從生成點開始計算，確保角色只會在連通的可行走區域內移動，防止角色「瞬間移動」到孤立的地圖區塊。
3. **路徑優化**：在 A* 算出原始路徑後，應用**共線節點移除（Collinear node removal）**與**視線剔除（Line-of-sight culling）**來平滑路徑，讓移動軌跡更自然。
4. **互動編排**：地圖中佈署了 8 個目標節點。點擊選單會驅動水豚移動至對應座標，到達後才會觸發內容視窗的開啟。

---

## 📂 專案結構

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
```
---

## 📄 License / 授權說明

本專案為個人作品集。美術素材源自 ClawLibrary，依其原始授權條款使用。

---


<p align="center">
<i>Built with ☕ and pixels by Wayne Chou</i>
</p>
