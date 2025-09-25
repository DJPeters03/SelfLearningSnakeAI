# Adjustable Snake RL — Control Guide (Plain English)

This guide explains the **left-side controls** so anyone can tweak the training without needing AI background.

---

## Environment

- **Board W×H**  
  The size of the grid the snake moves on (width × height). Bigger boards give more room; smaller boards make decisions tighter.

- **Max steps/episode**  
  A safety limit. If the snake wanders too long without finishing (dying or timing out), the round (episode) ends.

- **Speed (steps/sec)**  
  How fast the simulation runs (how many moves the snake takes per second). Raising this doesn’t make the snake “smarter,” it just runs more frames per second.

### Collisions
- **Walls kill (no wrap)**  
  When **ON**, hitting the edge ends the round (wall death).  
  When **OFF**, the board “wraps around” like a Pac‑Man tunnel (leaving one edge brings you in on the opposite side).

---

## Rewards (What the snake is paid or penalized for)

- **Fruit reward**  
  Points given when the snake eats a fruit. Higher means the snake is more motivated to find fruit.

- **Death penalty (self)**  
  Penalty when the snake runs into **its own body**.

- **Death penalty (wall)**  
  Penalty when the snake hits a **wall** (only relevant if “Walls kill” is ON).

- **Step (living) reward**  
  A tiny reward/penalty every move. Negative values encourage the snake to stop wasting time. Positive values encourage survival/wandering.

- **Distance shaping**  
  A small bonus (or penalty) each step based on getting **closer to the fruit** (bonus) or **farther** (penalty). Helps beginners learn faster.

- **Straightness bonus**  
  Small bonus when moving straight. Encourages smoother paths instead of jittery zig‑zags.

- **Starve steps**  
  If the snake goes this many steps without eating, the round ends (simulates “starvation”).

> **Timeouts:** If a round ends due to **max steps** or **starvation**, we apply a **mild penalty** equal to `0.25 × min(self, wall)` to gently discourage stalling without being too harsh.

---

## Algorithm (How learning updates happen)

- **Learning rate (α)**  
  How strongly we update what the snake “thinks” is good or bad after each step. Higher = learns faster but can overshoot; lower = steadier but slower.

- **Discount (γ)**  
  How much the snake values **future** rewards vs **right now**. Close to 1.0 means it plans ahead; lower values focus on the immediate move.

- **ε (epsilon) start → end** and **ε decay steps**  
  Epsilon controls **exploration** (trying random moves).  
  - **Start**: initial randomness (usually 1.0 = very explorative).  
  - **End**: the minimum randomness after decaying.  
  - **Decay steps**: how many total steps it takes to go from Start to End.

- **Reward clip (|r|≤1)**  
  Keeps rewards/penalties between -1 and +1 to stabilize learning.

---

## Run control

- **Run / Pause / Step**  
  Start, stop, or advance one move at a time.

- **Reset**  
  Restart the training with current settings.

- **Defaults**  
  Restore recommended starting values.

- **Seed**  
  A number that recreates the same random setup (fruit positions etc.). Use the same seed for repeatable tests.

---

## Overlays

- **Show sensors**  
  Draws short lines in front/left/right of the snake’s head to visualize what it’s “checking” for danger each step.

---

## Top Bar (Quick Stats)

- **Ep**: Episode (round) count.  
- **Step**: Steps in the current episode.  
- **Len**: Snake length (grows when it eats).  
- **Score**: Total fruits eaten in **this** episode.  
- **ε**: Current exploration amount (randomness).  
- **R/Ep (100-avg)**: Average total reward over the last 100 episodes (a rough learning gauge).  
- **SPS**: Steps per second (actual speed).  
- **Last end**: How the last episode ended (`self`, `wall`, `maxSteps`, or `starve`).

---

### Tips
- If the snake stalls: make **Step reward** more negative, lower **Starve steps**, or increase **Fruit reward**.  
- If it hugs walls: increase **Death penalty (wall)** or turn **Walls kill** ON.  
- For steadier behavior: lower **Learning rate**; for more daring behavior: raise **Epsilon start** or **Fruit reward**.
