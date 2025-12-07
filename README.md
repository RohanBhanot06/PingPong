# Ping Pong Game (Processing)

A two-player arcade-style **Ping Pong** game built in **Processing**.  
It includes a main menu, help/instructions screen, gameplay screen, and game-over screen.  
Two players share the keyboard and play up to **11 points**.

---

## Overview

This project is a classic **Pong-style** game created as part of an ICS2O1 course using the Processing environment.

Key features:

- Local **2-player** ping pong
- First to **11 points** wins
- Multiple **screens (stages)**:
  - Main menu
  - Help / instructions
  - Gameplay
  - Game over
  - Reset back to main menu
- Keyboard controls for each paddle
- Mouse-based UI buttons for navigating between screens
- Custom colours, font, and image assets

---

## Screens / Stages

The game uses a single `draw()` loop and a `stage` variable to control what is displayed:

- **Stage 0 – Main Menu**
  - Shows:
    - Game logo (`logo.jpeg`)
    - **Help** button (`help.png`)
    - **Play** button (`play.png`)
  - Clicking:
    - **Help** → goes to stage 1
    - **Play** → goes to stage 2

- **Stage 1 – Help Screen**
  - Shows:
    - Instructions image (`instructions.jpeg`)
    - **Back** button (`back.png`)
  - Clicking **Back** returns to **stage 0** (Main Menu).

- **Stage 2 – Play Screen**
  - Main gameplay:
    - Ball moves and bounces off:
      - Top & bottom borders
      - Left & right walls
      - Two paddles
    - Score is displayed at the top:
      - Left player score (`points1`)
      - Right player score (`points`)
    - When the ball passes:
      - **Left side** → right player gets a point
      - **Right side** → left player gets a point
    - When either score reaches **11**, game goes to **stage 3** (Game Over).

- **Stage 3 – Game Over Screen**
  - Shows:
    - Game logo (`logo.jpeg`)
    - Game over text (`gameOver.png`)
    - **Main Menu** button (`mainMenu.png`)  
  - Clicking the **Main Menu** button sets `stage = 4`.

- **Stage 4 – Reset Screen**
  - Resets:
    - Ball position
    - Paddle positions
    - Scores (`points` and `points1`)
  - Then returns to **stage 0** (Main Menu) to start again.

---

## Gameplay & Controls

### Objective

Be the first player to reach **11 points** by hitting the ball past your opponent’s paddle.

### Player Controls

- **Left Paddle (Player 1)**
  - Move **up**: `W`
  - Move **down**: `S`

- **Right Paddle (Player 2)**
  - Move **up**: `UP ARROW`
  - Move **down**: `DOWN ARROW`

### Mouse Controls (Menus)

- On the **Main Menu**:
  - Click on the **Help** image to view instructions.
  - Click on the **Play** image to start the game.

- On the **Help Screen**:
  - Click the **Back** image to return to the main menu.

- On the **Game Over Screen**:
  - Click the **Main Menu** image to reset and go back to the main menu.

---

## Core Mechanics

### Ball Movement

Variables:

- `bx`, `by` – ball position
- `vx`, `vy` – ball velocity
- `r` – ball radius

Each frame:

```java
bx = bx + vx;
by = by + vy;
