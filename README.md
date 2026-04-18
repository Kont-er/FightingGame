
# Fighting Game (Unity)

A 2D local multiplayer fighting game built in Unity, focusing on a modular frame-based combat system and animation-driven gameplay.

---

## Overview

This project implements a **frame-accurate fighting game system** designed for two players on a single machine with full controller support.

The focus is on creating a **modular and extensible gameplay framework**, where combat mechanics are separated from content, allowing new characters, animations, and moves to be added easily.

---
<img width="462" height="261" alt="Zrzut ekranu (1708)" src="https://github.com/user-attachments/assets/92992641-6763-44c7-bfd8-fbc94cb4b79b" />

---

## Features

* Local 2-player fighting gameplay
* Full controller support
* Frame-based combat system (startup, active, recovery frames)
* Unity Animator-driven state machine architecture
* Modular combo system based on frame data
* Round and match management system
* Extensible architecture for adding characters and moves

---

## Core Architecture

### Animation-Driven Combat

The game is built around Unity’s **Animator state machine system**, where gameplay actions are tightly linked to animation frames.

Key principles:

* Every move is defined by startup, active, and recovery frames
* Actions cannot be canceled once started
* State restrictions control available player actions (e.g. blocking, attacking, hitstun)

---

### State System

Gameplay logic is handled through multiple state scripts that respond differently depending on which player is active.

A central input driver system:

* Processes all player inputs
* Triggers animation state transitions
* Prevents invalid state changes during actions

Due to the complexity of possible states, multiple boolean flags are used to track player conditions.

---
<img width="1359" height="629" alt="Zrzut ekranu (1710)" src="https://github.com/user-attachments/assets/d2c4008b-a11d-4d98-91c1-7a78aae922cd" />

---


### Round Management

A dedicated game state controller manages match flow:

* Resets positions and states between rounds
* Tracks player scores
* Handles win conditions for matches

---

## Combat System

The combat system implements standard fighting game mechanics:

### Core interactions

* **Attacks vs Blocking** → Blocking wins
* **Throws vs Blocking** → Throws win
* **Reversal (invincible attacks)** → Beats attacks and throws, but is highly punishable

---

### Combo System

Combos are not hard-coded. Instead, they are determined by frame advantage and move properties.

* Each move defines its own timing and recovery
* Combo routes emerge dynamically from frame data
* System supports flexible and situational combo paths

---

## Special Mechanics

### Mark System

Certain attacks apply a **Mark** effect on hit:

* Enables additional follow-up options
* Used to extend combos and create advanced routes

---
<img width="372" height="284" alt="Zrzut ekranu (1711)" src="https://github.com/user-attachments/assets/79eb9770-7e73-4912-b4e7-20f8d402d801" />

---


### Design Philosophy

The gameplay system is designed to ensure:

* Every move has a defined purpose (pressure, zoning, combo, defense)
* No universally dominant option
* Strong risk/reward balance between actions

---

## Technical Design

### Input System

* Fully supports game controllers
* Designed for simultaneous two-player input on one device
* Centralized input handling system routes commands to gameplay logic



