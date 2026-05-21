# 🏝️ Cebu Conquest (セブ獲り合戦)

> A Real-Time Territory Capture & Turn-Based Battle Game set in Cebu, Philippines.

Cebu Conquest is a web-based multiplayer strategy game developed as the final flagship project for Kredo IT School Batch 21 AM. Players choose a local deity, strategize territory expansion, and battle opponents in real-time on a massive, interactive map of the Visayas region.

## 🚀 Key Features

* **Real-Time Multiplayer:** Synchronized state management and real-time battle resolution using Socket.IO.
* **Massive Interactive Map:** A 8000x9600px game board (250x300 tiles) featuring Cebu, Mactan, Negros, and Bohol.
* **Turn-Based Battle System:** Proportional probability battle calculations (P = A / (A + D)) executed securely on the Node.js server.
* **Deity & Buff System:** Choose from 8 local deities (e.g., Neil, Quisie) for unique starting bonuses and collect regional specialties for dynamic stat buffs.

## 🛠️ Technology Stack

**Frontend (Client)**
* **Game Engine:** Phaser 3.90.0 (Map rendering, Camera control, Battle effects)
* **UI/UX:** React 19, Vite 7, TypeScript
* **State Management:** Zustand 5
* **Map Design:** Tiled (TMJ format with embedded tilesets)

**Backend (Server)**
* **Real-Time Server:** Node.js, Express 5, Socket.IO 4.8.3 (Game logic, NPC AI)
* **REST API:** PHP (Vanilla), PDO, JWT Authentication
* **Database:** MySQL

## 🧠 Architecture & Technical Highlights (My Role: Project Leader / Frontend)

As the Project Leader and Frontend (Phaser) Developer, I tackled the following core challenges:

1. **LOD (Level of Detail) Zoom System & Rendering Optimization:**
   Rendering an 8000x9600px map natively caused performance bottlenecks. I implemented `ZoomManager.js` and `CameraController.js` to dynamically scale rendering detail based on the camera zoom level, ensuring a stable FPS across devices.
2. **Decoupled React-Phaser Architecture:**
   To prevent memory leaks and state desynchronization, I designed `PhaserBridge.js`. This module strictly defines event constants (e.g., `PHASER_TO_REACT.STATS_UPDATED`) and completely eliminates raw `window.dispatchEvent` calls, ensuring a safe, event-driven data flow between the game canvas and the React HUD.
3. **Single Source of Truth (SSOT) Management:**
   To align a team of 4 across different tech stacks, we established a strict "ID Management Sheet". Critical game data like Adjacency graphs (`shared/adjacency.js`) and Deity Spawns (`shared/godSacredLands.js`) were strictly shared between the Node.js server and the Vite client to prevent conflicts.

## 🤝 Team Git Workflow

To prevent merge conflicts during concurrent development across 4 specialized branches, our team adhered to the following strict PR sequence:
1. Commit work to the local feature branch (e.g., `feature/akira-phaser-*`).
2. Switch to the local `main` branch and pull the latest code.
3. Merge the updated `main` into the feature branch locally.
4. Resolve any conflicts and reinstall Node Modules if necessary.
5. Ensure a clean working directory (no pending changes), push to GitHub, and open a Pull Request.

## 👥 Team Structure
* **Akira (Project Leader):** Phaser.js, Map Design, UI/UX, Project Management
* **Issei:** React, Vite, TypeScript, Zustand, HUD
* **Kei:** Socket.IO, Node.js, Battle Calculations, Server State
* **Nao:** PHP, MySQL, REST API, DB Schema