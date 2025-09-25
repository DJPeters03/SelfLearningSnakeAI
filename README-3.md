# Snake RL Package

This package contains **two interactive reinforcement learning snake games**, each with a different purpose:

---

## 1. Snake vs AI (Real-Time Duel)

- **File:** `SnakeVsAI.html`  
- **What it is:** A classic **Snake** game where a **human player** directly plays against a **self-learning AI snake** in real time.  
- **Goal:** Compete to collect fruit and survive longer.  
- **Key feature:** You get to **see the AI adapt** and compare your strategies against it as you play.

---

## 2. Adjustable Snake RL (Training Sandbox)

- **File:** `AISnakeWithControls.html`  
- **What it is:** A **sandbox** to train a self-learning snake (via Q-learning).  
- **Controls:** A full side panel lets you adjust:
  - **Environment** (board size, wall wrap, max steps, speed).  
  - **Rewards** (fruit reward, penalties for self/wall death, shaping bonuses, etc.).  
  - **Algorithm parameters** (learning rate, discount factor, epsilon exploration settings).  
  - **Run controls** (start, pause, step, reset).  
- **Goal:** Understand how different reinforcement learning settings affect training.  
- **Learning:** You can **see in real time** how the snake’s policy improves, stalls, or collapses depending on the parameters you pick.

> For a plain-English explanation of each control, see **`ControlsGuide.md`**, which explains every option without requiring AI background knowledge.

---

## How to Use

1. Open either HTML file in a modern browser (Chrome, Firefox, Safari, or Edge).  
2. Use keyboard or UI controls depending on the game.  
3. Adjust settings in the sandbox to experiment with reinforcement learning concepts.

---

## Educational Value

- **Snake vs AI:** Lets you *feel* how an AI opponent plays and evolves.  
- **Adjustable RL Snake:** Lets you *control the knobs* of reinforcement learning to see cause and effect in a live environment.  

Together, these files provide both a **hands-on game experience** and a **teaching tool** for understanding reinforcement learning.
