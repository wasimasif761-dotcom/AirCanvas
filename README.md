# 🎨 AirCanvas — AI-Powered In-Air Finger Drawing

> Draw in the air with your index finger using your webcam and on-device MediaPipe AI hand tracking. Zero servers. 100% client-side. Offline-first PWA.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
[![PWA Ready](https://img.shields.io/badge/PWA-Ready-10b981.svg)](#-progressive-web-app-pwa)
[![AI Engine](https://img.shields.io/badge/AI-MediaPipe%20Hands-06b6d4.svg)](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker)
[![Offline Capable](https://img.shields.io/badge/Offline-100%25%20On--Device-8b5cf6.svg)](#-privacy--offline-architecture)

---

## ✨ Overview

**AirCanvas** turns your webcam into an interactive digital canvas. By detecting hand landmarks in real-time, it tracks the tip of your index finger (**Landmark 8**) as a brush tip, allowing you to paint neon strokes, sketch ideas, or write in thin air.

Everything runs entirely in your browser using Google MediaPipe's WebAssembly models — **no webcam images are ever uploaded or transmitted over the internet**.

---

## ✋ Hand Gestures Guide

AirCanvas recognizes your natural hand poses to switch seamlessly between drawing, navigating, and resting:

| Gesture | Pose | Mode | Action |
| :---: | :---: | :---: | :--- |
| ☝️ | **1 Finger Up**<br>*(Index UP, Middle DOWN)* | **Draw Mode** | Lays down smooth ink strokes at your index fingertip. |
| ✌️ | **2 Fingers Up**<br>*(Index UP & Middle UP)* | **Hover / Move Mode** | Moves the glowing reticle cursor **without** drawing ink, allowing you to reposition your hand. |
| ✋ / ✊ | **Open Palm or Fist**<br>*(All fingers up / closed)* | **Pause Mode** | Pauses tracking so you can rest your hand without accidental marks. |

> **Tip:** If you don't have a webcam or camera access is restricted, AirCanvas includes a built-in **Virtual Hand AI Simulation** and **Mouse/Touch Canvas Mode** so you can test and use the app immediately!

---

## 🚀 Key Features

- **🎯 Precision Fingertip Tracking:** Tracks MediaPipe landmark 8 with Exponential Moving Average (EMA) smoothing to eliminate micro-tremors and produce silky lines.
- **🪞 Mirrored Real-Time Feed:** Video stream is mirrored horizontally (`scaleX(-1)`) so gestures feel natural like looking into a mirror.
- **🎛️ Floating Cyber HUD:**
  - **Color Palette:** Red, Blue, Green, Black, Neon Cyan, Neon Yellow, Neon Purple, White, plus a custom RGB Color Picker.
  - **Brush Styles:**
    - `Glow` — Cyberpunk neon glow with bright core.
    - `Solid` — Crisp, opaque digital ink.
    - `Marker` — Translucent highlighter.
  - **Brush Size Slider:** Smooth 2px to 40px adjustment with a live dot preview.
  - **Eraser Mode:** Removes strokes with custom eraser width.
  - **Webcam Opacity Control:** Dial background visibility from 0% (pure dark canvas) to 100% (full webcam backdrop).
  - **Skeleton Mesh HUD:** Toggle on-screen joint skeleton overlay on/off.
- **↩️ Undo / Redo & Clear:** Full snapshot history with keyboard shortcuts (`Ctrl+Z` / `Ctrl+Y`).
- **📸 Smart Download:** Merges your mirrored webcam frame and drawing into a single high-resolution PNG image with a timestamp badge.
- **📱 PWA & 100% Offline:** Embedded data-URI manifest and Service Worker for instant offline installation on desktop and mobile.

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
| :--- | :--- |
| `Ctrl + Z` / `Cmd + Z` | Undo last stroke |
| `Ctrl + Y` / `Cmd + Y` or `Ctrl + Shift + Z` | Redo stroke |
| `Spacebar` *(in Virtual Hand mode)* | Toggle between Draw and Hover gestures |

---

## 🛠️ Tech Stack

- **Computer Vision:** `@mediapipe/hands`, `@mediapipe/camera_utils`, `@mediapipe/drawing_utils` (via CDN)
- **Styling:** Tailwind CSS (Dark Futuristic Cyber Theme)
- **Graphics:** HTML5 2D Canvas API with sub-pixel Bézier interpolation
- **Runtime & Build:** Vite + TypeScript
- **PWA:** Service Worker caching + embedded Web App Manifest

---

## 💻 Getting Started Locally

### Option 1: Run with Vite Dev Server (Recommended)

```bash
# 1. Clone the repository
git clone https://github.com/saadwaseem6161/aircanvas.git

# 2. Navigate into the folder
cd aircanvas

# 3. Install dependencies
npm install

# 4. Start development server
npm run dev
```

Open your browser at `http://localhost:3000`.

### Option 2: Build for Production

```bash
npm run build
npm run preview
```

The production-optimized files will be output to the `dist/` directory.

### Option 3: Zero-Build Standalone Run

Because AirCanvas is built as a self-contained single-file PWA, you can also open `index.html` directly in any modern browser with webcam access (via `npx serve`, Python `python -m http.server`, or VS Code Live Server).

---

## 🌐 Deploying to GitHub Pages

1. In your GitHub repository, go to **Settings** > **Pages**.
2. Under **Build and deployment**:
   - Set **Source** to **Deploy from a branch** or use **GitHub Actions**.
   - If deploying built output, push the `dist/` branch or use the automated GitHub Action workflow provided in `.github/workflows/deploy.yml`.
3. Your app will be live at `https://<your-username>.github.io/aircanvas/`!

---

## 🔒 Privacy & Offline Architecture

AirCanvas is built with privacy at its core:
- **No telemetry, analytics, or user accounts.**
- **No external API calls:** MediaPipe models run directly in browser WebAssembly.
- **Webcam security:** Your camera video feed stays strictly in browser memory and is never recorded, streamed, or uploaded to any cloud server.

---

## 📄 License

This project is licensed under the [MIT License](./LICENSE) — free for personal and commercial use.
