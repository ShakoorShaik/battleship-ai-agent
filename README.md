# Nautica — Most Creative Implementation, Code Clash UofT Winter 2026

**Nautica** is an autonomous AI bot built by **gervigreind** for the **Code Clash: Battleship Challenge** at the University of Toronto. The project demonstrates algorithmic strategy design, robust systems programming, and competition-grade AI engineering under strict real-time constraints.

---

## Overview

| Attribute | Detail |
|---|---|
| Game | Enhanced Battleship (8x8 grid, 4 ships, special abilities) |
| Environment | Headless, turn-based AI competition |
| Constraints | Single executable file, 3-second move limit, no external dependencies |
| Evaluation | Win/loss record with bonus credit for creative strategies |

The bot autonomously selects abilities, places ships, and executes combat decisions against opposing AI agents.

---


## AI Strategy

### Ability Selection

Nautica uses a heuristic scoring function to evaluate and select abilities at each decision point. The scoring model maximizes two objectives: **information gain** (board reveal potential) and **action efficiency** (shots per turn). This establishes early- and mid-game advantage through probability-based board reasoning.

### Ship Placement

Ship placement follows deterministic, rule-safe logic designed to minimize exposure to area-of-effect attacks and reduce predictability against common targeting heuristics such as heat-map scanning and edge-priority strategies.

### Combat Logic

The combat system implements an enhanced **Hunt-and-Target** algorithm:

**Hunt Mode** — Searches unexplored cells using a lightweight probability density map, avoiding low-value or already-eliminated regions.

**Target Mode** — Triggered on a confirmed hit. Prioritizes adjacent cells consistent with ship geometry and continues until the target ship is fully sunk.

Additional decision rules prevent redundant shots and gate special ability usage behind an expected-value threshold — abilities are only deployed when their projected value exceeds that of a standard attack.

No machine learning was used. The strategy favors interpretable, deterministic algorithms appropriate for time-critical systems.

---

## Algorithms and Methodologies

- Heuristic-based decision making
- Lightweight probability density mapping (non-ML)
- Hunt-and-Target combat algorithm
- Expected value comparison for ability selection
- Defensive programming with fallback logic for edge-case states

---

## Technical Stack

**Language:** Python 3

**Libraries (standard library only):**
- `json` — game state parsing and output formatting
- `sys` — CLI integration
- `random` — controlled stochastic decisions

No third-party dependencies (per competition requirements).

---

## Architecture

The bot is structured as a single-file executable that interfaces with the provided competition API abstraction (`battleship_api.py`) for game state decoding, move validation, and protocol compliance. Defensive logic handles malformed or edge-case game states gracefully.

---

## Project Structure

```
.
├── battleship_bot.py   # AI bot (submission file)
├── battleship_api.py   # Competition-provided API
└── README.md
```

---

## Usage

```bash
python3 battleship_bot.py /path/to/state.json
```

The bot reads the current game state, determines the active phase (placement, ability selection, or combat), and outputs exactly one valid JSON move to stdout.
