# Hand Tracking Piano

**Live demo:** https://shreyajainnx09.github.io/Hand-Tracking-PIano-AR/

## Description
A browser-based augmented reality piano that uses your webcam and hand-tracking to let you "play" piano keys in mid-air. Hover any fingertip over an on-screen key and it plays — no physical keyboard or MIDI hardware required.

## Features
- Real-time hand/fingertip tracking via webcam
- On-screen piano keys mapped to physical hand position
- Fully client-side — no installs, runs directly in the browser
- Zero setup: camera initializes automatically on page load

## Tech Stack (typical for this kind of project — adjust to match your actual repo)
- HTML5 / CSS3 / JavaScript
- A hand-tracking library (e.g. MediaPipe Hands or a similar computer-vision model)
- Webcam access via `getUserMedia`

## How It Works
1. The page requests camera permission and initializes video capture.
2. A hand-tracking model detects fingertip landmarks each frame.
3. Fingertip coordinates are mapped onto the piano key layout.
4. When a fingertip overlaps a key's bounding area, the corresponding note plays.

## Getting Started
```bash
git clone https://github.com/shreyajainnx/AR.git
cd AR
# open index.html in a browser, or serve locally:
python3 -m http.server 8000
```
Then visit `http://localhost:8000` and allow camera access.

## Usage
- Allow camera permissions when prompted.
- Hold your hand up in front of the camera.
- Move a fingertip over any key to play its note.

## Roadmap Ideas
- Multi-hand / multi-note chords
- Recording and playback
- Custom instrument sounds
- Mobile camera support

## Author
Shreya Jain
