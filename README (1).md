# 🍉 Blade Dojo — Hand-Tracking Fruit Slicer

A browser-based fruit-slicing game inspired by Fruit Ninja — controlled entirely with your **index finger** via real-time webcam hand tracking. No installs, no build tools, no backend. Just open it in a browser.

![tech](https://img.shields.io/badge/stack-Vanilla%20JS-yellow) ![tech](https://img.shields.io/badge/rendering-Canvas%202D-blue) ![tech](https://img.shields.io/badge/tracking-MediaPipe%20Hands-green) ![tech](https://img.shields.io/badge/audio-Web%20Audio%20API-orange)

---

## ✨ Features

- **Real-time hand tracking** — [MediaPipe Hands](https://github.com/google/mediapipe) tracks your index fingertip and turns it into a glowing blade
- **Fallback controls** — no webcam? The game seamlessly falls back to mouse/touch input
- **3 game modes**
  - **Classic** — 3 lives, bombs end the run instantly
  - **Zen** — 90 seconds, no bombs, no lives, just score
  - **Arcade** — 60-second timer, bombs cost points instead of lives, combo-driven scoring
- **Physics-based slicing** — fruit splits into two halves with gravity, rotation, and juice-particle bursts
- **Synthesized audio** — every sound effect (slice, bomb, combo, game over) is generated live with the Web Audio API — no audio files
- **Persistent high scores** — saved per-mode in `localStorage`
- **Glowing blade trail** with fading particles, rendered entirely on HTML5 Canvas

## 🧱 Tech Stack

| Purpose | Technology |
|---|---|
| Logic | Vanilla JavaScript (no frameworks) |
| Rendering | HTML5 Canvas (2D context) |
| Hand tracking | Google MediaPipe Hands (CDN) |
| Camera feed | `getUserMedia` API |
| Audio | Web Audio API (synthesized, no audio assets) |
| Game loop | `requestAnimationFrame` |
| Persistence | `localStorage` |

## 🚀 Getting Started

Webcam access is blocked by browsers on plain `file://` pages, so the game needs to be served from a local (or hosted) web server.

### Option 1 — Python

```bash
git clone https://github.com/MidhunaSp/ninja_fruitblade.git
cd ninja_fruitblade
python3 -m http.server 8000
```

Then open **http://localhost:8000/blade-dojo.html** and allow camera access when prompted.

### Option 2 — Node

```bash
npx serve .
```

### Option 3 — VS Code

Use the **Live Server** extension and click "Go Live" on `blade-dojo.html`.

> An internet connection is required even when running locally, since MediaPipe's model files are loaded from a CDN.

## 🎮 How to Play

1. Choose a **game mode** (Classic / Zen / Arcade)
2. Choose your **input**: Webcam Hand Tracking or Mouse / Touch
3. Click **Start Game**
4. If using webcam: hold your hand up so your **index finger** is visible — the fingertip becomes the blade
5. **Swipe through fruit** to slice it. Avoid the bombs (💣) unless you're in Arcade mode (where they just cost points)

### Keyboard shortcuts

| Key | Action |
|---|---|
| `P` | Pause / Resume |
| `Esc` | Return to menu |
| `M` | Mute / Unmute |

## 📁 Project Structure

```
ninja_fruitblade/
└── blade-dojo.html   # entire game — HTML, CSS, and JS in a single file
```

The file is organized into clearly commented sections:

```
CONFIG          → game constants, fruit types, mode definitions
AUDIO           → Web Audio–based sound engine
HAND TRACKING   → MediaPipe Hands integration + smoothing
INPUT           → unifies hand tracking with mouse/touch fallback
ENTITIES        → fruit / bomb / particle / popup factories
COLLISION       → point-to-segment swipe collision detection
GAME ENGINE     → update loop, physics, scoring, spawner
RENDERER        → all canvas drawing
UI MANAGER      → screens, HUD, high scores
BOOTSTRAP       → wires everything together on load
```

## 🛠️ Browser Requirements

- A modern browser (Chrome, Edge, or Firefox recommended) with webcam support
- HTTPS or `localhost` (required by `getUserMedia`)
- Camera permission granted when prompted

## 🙏 Credits

- [MediaPipe Hands](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker) — Google, hand landmark tracking
- Web Audio API — all sound effects synthesized in-browser, no external assets

## 📄 License

Add a license of your choice (MIT recommended for a personal/demo project).
