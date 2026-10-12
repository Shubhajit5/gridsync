<div align="center">

  # 🚦 GridSync: Smart City Traffic Grid Simulator

  **An interactive HTML5 Canvas traffic simulation featuring real-time adaptive AI signal switching and telemetry logging.**

  [![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
  [![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
  [![Canvas API](https://img.shields.io/badge/Canvas_API-000000?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

</div>

---

## 📌 Overview

**GridSync** is an interactive, browser-based smart traffic grid simulation. It models 2D vehicle kinematics at a 4-way intersection, comparing traditional **Fixed Timer** traffic lights against an **Adaptive AI** signal controller. The adaptive algorithm dynamically monitors stopped vehicle queue lengths in real time to minimize congestion and balance cross-traffic corridors.

---

## ✨ Key Features

* **🧠 Adaptive AI vs. Fixed Timer Modes:** Switch on the fly between standard timed light cycles and queue-length-driven adaptive signal switching.
* **🚗 Dynamic Vehicle Kinematics:** Simulates vehicle spawning, stop-line detection, collision buffering between leading vehicles, and variable car color rendering.
* **💥 Traffic Surge Injection:** Manual trigger to spawn sudden traffic surges across North, South, East, and West corridors to stress-test the intersection.
* **📊 Live Telemetry & Logging:** Real-time console box displaying timestamped signal phase changes, mode switches, and active vehicle counts.
* **🎨 Dark Cyberpunk Aesthetic:** Dark-mode canvas visuals with realistic road paint, stop lines, animated vehicles, and status indicators.

---

## 🛠️ Tech Stack

* **Frontend:** Vanilla HTML5, CSS3
* **Rendering Engine:** HTML5 2D Canvas API
* **Logic:** Vanilla JavaScript (ES6+ Classes, RequestAnimationFrame animation loop)

---

## 🏗️ How the Adaptive AI Signal Works

The simulation checks queue lengths on both North-South ($NS$) and East-West ($EW$) corridors:

```mermaid
graph TD;
    A[Monitor Active Queue Lengths] --> B{Is Adaptive Mode Active?};
    B -- Yes --> C{Opposing Queue > 2 Vehicles & Timer > Threshold?};
    C -- Yes --> D[Trigger Instant Light Cycle Switch];
    C -- No --> E[Maintain Current Light State];
    B -- No --> F[Cycle Light on Fixed Interval];
