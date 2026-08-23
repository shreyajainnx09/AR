<div align="center">

# 🎹 Hand Tracking Piano AR
### A browser-based AR piano you play with just your webcam

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-00897B?style=for-the-badge&logo=google&logoColor=white)](https://img.shields.io/badge/MediaPipe-00897B?style=for-the-badge&logo=google&logoColor=white)
[![Web Audio API](https://img.shields.io/badge/Web%20Audio%20API-black?style=for-the-badge&logo=webaudioapi&logoColor=white)](https://img.shields.io/badge/Web%20Audio%20API-black?style=for-the-badge&logo=webaudioapi&logoColor=white)
[![Play Now](https://img.shields.io/badge/🎮%20PLAY%20IN%20BROWSER-6C3EB8?style=for-the-badge)](https://shreyajainnx09.github.io/Hand-Tracking-PIano-AR/)

</div>

---

## 📌 Description

A browser-based **augmented reality piano** you play by hovering your fingertips over on-screen keys — using real-time webcam hand-tracking. No physical keyboard, no MIDI hardware, no install. Just open the page, allow camera access, and start playing.

- Real-time fingertip tracking via **MediaPipe Hands**, tracking up to 2 hands at once
- A one-octave piano (C4–C5, white + black keys) rendered live on an HTML5 `<canvas>`, overlaid on your mirrored webcam feed
- Actual synthesized notes played through the **Web Audio API** (triangle oscillator with a short envelope) — no audio samples needed
- Visual hand skeleton overlay showing all 21 tracked hand landmarks, with fingertips highlighted
- Per-note cooldown so a held fingertip doesn't spam-retrigger the same note every frame
- **[Play it live](https://shreyajainnx09.github.io/Hand-Tracking-PIano-AR/)** — no install needed, works right in the browser

## 🎮 How to Play

1. Open the [live demo](https://shreyajainnx09.github.io/Hand-Tracking-PIano-AR/) and allow camera access.
2. Hold your hand(s) up in front of your webcam.
3. Move any fingertip over a piano key on screen — it plays the moment it hovers over it.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| 🌐 HTML5 / Canvas | Rendering the piano, video feed, and hand skeleton |
| 🟨 JavaScript | App logic, key-collision detection, note triggering |
| ✋ MediaPipe Hands | Real-time hand/fingertip landmark tracking (loaded via CDN) |
| 🔊 Web Audio API | Synthesizing piano notes on the fly (no audio files) |

## ⚙️ Setup

No build step or dependencies to install — it's a single static HTML file.

```bash
git clone https://github.com/shreyajainnx09/Hand-Tracking-PIano-AR.git
cd Hand-Tracking-PIano-AR
python3 -m http.server 8000
```

Then open `http://localhost:8000` in your browser and allow camera access. (Opening `index.html` directly by double-clicking may also work, but serving it locally avoids browser camera-permission quirks.)

## 🧠 How It Works

- `getUserMedia` requests webcam access and streams video into a hidden `<video>` element
- **MediaPipe Hands** processes each video frame and returns 21 hand landmarks per detected hand (up to 2 hands)
- `getKeyRects()` computes the pixel bounding boxes for all 8 white keys (C4–C5) and 5 black keys based on canvas size
- `checkFingerOnKeys()` checks all 5 fingertip landmarks (thumb, index, middle, ring, pinky) per hand against those key boxes — black keys are checked first since they render on top
- On a hit, `playNote()` creates a short-lived triangle-wave oscillator through the Web Audio API to produce the tone, with a per-note cooldown (400ms) to prevent re-triggering every animation frame
- `drawSkeleton()` draws the hand connections and joints (MediaPipe's 21-point hand model) as a translucent overlay on the mirrored video feed
- Everything renders in a single `requestAnimationFrame` loop: clear canvas → draw mirrored video → draw hand skeletons → draw the piano (highlighting any currently-active keys)

## 📁 Project Structure

```
Hand-Tracking-PIano-AR/
│
├── index.html       → Entire app — markup, styling, and all JS logic in one file
└── README.md
```

## 🌟 Ideas for Extending

- Multi-octave keyboard (currently fixed to one octave, C4–C5)
- Chord detection when multiple fingertips land on keys simultaneously
- Recording and playback of what you've played
- Alternate instrument sounds (different oscillator types or sampled tones)
- Visual "sheet music" mode that highlights which key to hit next

## 👩🏻‍💻 Author

**Shreya Jain**
BCA | Data Analytics | Python | SQL | Tableau
