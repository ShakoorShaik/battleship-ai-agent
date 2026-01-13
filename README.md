# 🛳️ Winner of Most Creative Implementation @ Code Clash UofT Winter 2026

**Nautica**, by **gervigreind** (Team Name), is an 🤖 **Autonomous AI bot** built for the **Code Clash: Battleship Challenge** at the **University of Toronto**. This project highlights **algorithmic strategy design**, **robust systems programming**, and **competition-grade AI engineering** under strict real-time constraints of 10 hours.

---

## 🎯 Overview

* 🎮 **Game:** Enhanced Battleship (8×8 grid, 4 ships, special abilities)
* ⚙️ **Environment:** Headless, turn-based AI competition
* ⏱️ **Constraints:** Single executable file, ≤3s per move, no external dependencies
* 🏆 **Evaluation:** Win/Loss record + bonus for creative strategies

The bot autonomously selects abilities, places ships, and executes combat decisions against other AI agents.

---

## 🧠 Core AI Strategy

### 🌀 Ability Selection

Uses a **heuristic scoring function** to select abilities that maximize:

* 📊 **Information gain** (board reveal potential)
* 🎯 **Action efficiency** (shots per turn)

This establishes early- and mid-game advantage using **probability-based board reasoning**.

---

### 🚢 Ship Placement

* Deterministic, rule-safe placements
* 🛡️ Minimizes exposure to area-of-effect attacks
* 🎭 Reduces predictability against common targeting heuristics

Placement logic is designed to resist naive heat-map and edge-scanning strategies.

---

### ⚔️ Combat Logic

Implements a classic **Hunt → Target algorithm** enhanced with heuristics:

* 🔍 **Hunt Mode:**

  * Searches unexplored cells using a lightweight **probability density map**
  * Avoids low-value or already-eliminated regions

* 🎯 **Target Mode:**

  * Triggered after a confirmed hit
  * Prioritizes adjacent cells consistent with ship geometry
  * Continues until the ship is fully sunk

Additional decision rules:

* ❌ Avoids redundant or low-value shots
* ⚡ Deploys abilities only when their **expected value exceeds a standard attack**

This results in an efficient, adversarially-aware firing strategy without brute-force search.

---

## 🧩 Algorithms & Methodologies Used

* 🧠 **Heuristic-Based Decision Making**
* 📈 **Probability Mapping (Lightweight, Non-ML)**
* 🎯 **Hunt-and-Target Battleship Algorithm**
* ⚖️ **Expected Value Comparison for Ability Usage**
* 🛑 **Defensive Programming & Fallback Logic**

No machine learning was used—favoring **interpretable, deterministic algorithms** suitable for time-critical systems.

---

## 🛠️ Technical Stack

### 💻 Language

* **Python 3**

### 📚 Libraries (Standard Only)

* `json` – game state parsing & output
* `sys` – CLI integration
* `random` – controlled stochastic decisions

🚫 No third-party dependencies (competition requirement).

---

## 🏗️ Architecture

* 📦 Single-file executable bot: `battleship_bot.py`
* 🔌 Uses provided API abstraction (`battleship_api.py`) for:

  * Game state decoding
  * Move validation
  * Protocol compliance
* 🛡️ Defensive logic to handle malformed or edge-case states safely

---

## 📂 Project Structure

```
.
├── battleship_bot.py   # Final AI bot (submission file)
├── battleship_api.py          # Provided competition API
└── README.md                  # Project documentation
```

---

## 🚀 Running the Bot

```bash
python3 battleship_bot.py /path/to/state.json
```

The bot reads the game state, determines the current phase, and outputs **exactly one valid JSON move**.

##
