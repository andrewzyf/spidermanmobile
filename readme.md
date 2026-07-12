# WEBRUNNER II — Swing the Skyline (Mobile Edition)

An immersive, lightweight, physics-driven 3D web-swinging sandbox game built entirely in vanilla HTML5 and **Three.js**. Navigate a sprawling Manhattan-inspired procedural island featuring skyscrapers, central parks, moving traffic, and architectural landmarks under a cinematic dusk sky. 

This repository adapts the original, high-octane desktop mechanics into a seamless mobile-first layout utilizing screen-dragging and virtual buttons, while retaining 100% full desktop backwards compatibility.

---

## 📱 Mobile Controls
The HUD layout has been optimized for dual-thumb mobile play. The bottom half of the screen handles inputs, while the top half tracks your performance metrics.

* **Look / Steer:** **Drag your finger** anywhere on the screen (outside of the buttons) to look around. The hero automatically steers and leans toward your camera trajectory.
* **Web Swing:** **Hold the `SWING` button** on the left. The web will anchor onto the nearest valid structure in your field of view.
* **Dive (Build Momentum):** **Hold the `DIVE` button** on the right to accelerate downward, allowing you to convert gravitational pull into extreme forward velocity.
* **Jump / Run:** **Tap or hold the `JUMP / RUN` button** on the right. When grounded, it acts as a directional run toggle or jumps.
* **Reset:** **Tap the `R` button** in the top-right corner if you fly out into the open ocean or get wedged between architecture.
* **Reticle Status:**
  * **White Dot:** Valid anchor in range.
  * **Red Dot:** Open water, empty sky, or too far from a building. *Webs will fail to anchor.*

---

## 💻 Desktop Controls
If played on a desktop browser, the mobile interface hides itself or coexists smoothly alongside standard keyboard and mouse inputs:

| Action | Control |
| :--- | :--- |
| **Look / Aim** | Mouse Move (Pointer Lock) |
| **Shoot & Hold Web** | Left Mouse Button (LMB) *or* Spacebar |
| **Release Web** | Let go of LMB *or* Spacebar |
| **Dive (Speed Burst)**| Hold `Shift` |
| **Extra Turning Leans**| `A` / `D` keys |
| **Ground Jump** | `Spacebar` while standing |
| **Reset Simulation** | `R` key |

---

## 🛠️ Mobile Technical Enhancements
To achieve a native app-like experience within a mobile web browser, the codebase includes several critical performance and design updates:

* **Viewport Rigidness:** Uses `touch-action: none` and `overscroll-behavior: none` to entirely block default browser gestures like pinch-zooming, rubber-banding, or swipe-to-refresh.
* **Multi-Touch Integration:** The input handlers support independent touch loops, meaning players can simultaneously hold the `SWING` button with their left thumb while active-dragging the screen with their right thumb to loop and steer around corners.
* **Optimized Pixel Ratio:** Device pixel scaling is capped at `Math.min(devicePixelRatio, 2)` to prevent modern high-density screens (like Retina displays) from choking GPU rendering while preserving crisp UI elements.
* **Web Audio Wakeup:** Audio contexts are tied directly to the first touch interface interaction (`touchstart`), clearing strict browser security policies automatically.

---

## 🏗️ Architectural Summary
* **Graphics Core:** Three.js Custom Shader Materials for performance-friendly procedural lit building facades and an integrated atmospheric dusk sky dome.
* **Physics Engine:** Custom one-sided distance constraint loop with dynamic arc-bottom momentum pumps, structural box collision boxes, and ground frictional dampening.
* **Asset Loading:** Completely standalone. The only external resource is a CDN-hosted copy of `three.min.js`.

---

## 🚀 Quick Start
1. Save the source code into an `index.html` file.
2. Open the file directly inside any mobile browser (Safari, Chrome) or host it using a quick local server:
   ```bash
   npx serve .
   ```
3. Tap **ANYWHERE TO PLAY** on the loading splash card to initialize the audio context and start your run.
