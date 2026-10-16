# Lab 4: VibeCoding, Simple Platformer

**Project repo (code and per-task commits):** https://github.com/harish-rameshkumar/44_simple-platformer
**Lab repo (this repo):** https://github.com/harish-rameshkumar/SE_Labs

## Problem statement

A partially working Pygame platformer was provided. It had a collision bug and was missing several features. The goal of this lab was to use an AI coding tool (Claude Code) as a pair-programming partner to fix the bug and add the features one task at a time, with a separate commit for each task.

| Task | Requirement |
|------|-------------|
| 1 | Fix collision detection: the player sometimes fell through platforms after a long fall |
| 2 | Add a Game Over screen showing the final score (fall off the bottom or touch the hazard) that waits for input instead of printing to the console |
| 3 | Add a replay option with a choice of Easy, Medium or Hard difficulty (gravity and jump strength), or exit |
| 4 | Add sound effects for jumping, reaching the goal and dying |

## What was done

- **Task 1:** The cause was that gravity had no maximum speed and collision only compared positions after the move, so a fast fall could skip past a thin platform. I added a maximum fall speed and a swept landing check that compares the player's previous bottom edge with the platform top.
- **Task 2:** A Game Over overlay drawn in the Pygame window shows the final score. It is triggered by a hazard hit or a fall off the bottom. Input is ignored for about half a second after death so a held key does not skip the screen.
- **Task 3:** On Game Over the player presses 1, 2 or 3 to replay on Easy, Medium or Hard (each sets gravity and jump strength), or Esc/Q to exit. Replay resets the score and player state.
- **Task 4:** Sounds for jump, goal and death are synthesized in code (`game/sound.py`), so there are no audio files. If audio cannot start, the game keeps running silently.

## How to run

    pip install -r code/requirements.txt
    cd code
    python main.py

Controls: Left/Right or A/D to move, Space/Up/W to jump. On Game Over: 1/2/3 to replay (Easy/Medium/Hard), Esc or Q to exit.

## Deliverables in this folder

| File | Description |
|------|-------------|
| `before.mov` | 10-second video of the original game showing the fall-through bug |
| `after.mov` | 10-second video after the fixes, showing landing, Game Over, replay and the goal |
| `chat-history.pdf` | Exported Claude Code conversation |
| `code/` | Final game code |

## AI tool used

Claude Code (Anthropic), used as the AI pair-programming partner as the lab requires.

## Commit history

Each task was committed separately in the project repo: https://github.com/harish-rameshkumar/44_simple-platformer/commits/main
