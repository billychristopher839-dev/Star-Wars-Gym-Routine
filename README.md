# George Lucas: Road to #1 — A Star Wars Training Saga

A gamified 30-day beginner exercise tracker, themed around Star Wars. You play **George Lucas**, building your saga one workout at a time. Log a full day of training to earn **+8 points** and unlock a new character — each stronger than the last — and climb the galaxy leaderboard from a nobody in the Outer Rim all the way to **#1, the most powerful in the galaxy**.

Everything lives in a single `index.html`. No build step, no external files, no internet required. The Star Wars theme music and logo are embedded directly in the page.

## How to play

1. Open the page and go through the one-time onboarding crawl (set your name, acknowledge the mission).
2. Each day, head to the **Train** tab and check off all nine exercises in your routine.
3. Hit **Log today's training** — the theme plays, you bank **+8 points**, and the day's character is unlocked.
4. Miss a day and you lose **5 points**, so keep the streak alive.
5. Reach **204 of 240 points** (85%) to claim **#1 in the galaxy**.

### The routine (First Interval)

1. Wall Sit — 30s × 3
2. Calf Raises — 30 × 3
3. Forearm (Low) Plank — 30s × 3
4. Half Push-Up
5. Squat
6. Loosening Up (random / Muay Thai / elbow / boxing)
7. Knee Kick
8. One-Foot Exercise
9. Stretching

The routine is fully editable in-app — add, remove, rename, or reset to the default First Interval.

## Tabs

- **Holocron** — how the game works, the rules, and a preview of your routine.
- **Train** — your daily checklist, completion ring, and the log button.
- **Roster** — all 30 characters, locked until you earn them.
- **Progress** — stats, the 30-day saga grid, the galaxy leaderboard ladder, recent activity, and settings (rename, reset, sound).

## Deploying to GitHub Pages

1. Create a repository and add `index.html`, `.nojekyll`, and this `README.md`.
2. In **Settings → Pages**, set the source to your main branch, root folder.
3. The `.nojekyll` file is included so GitHub serves the file as-is (no Jekyll processing).
4. Visit the published URL. After any update, hard-refresh with **⌘⇧R** (Mac) to bust the cache.

## Notes

- Progress is saved locally in your browser (`window.storage` → `localStorage` → in-memory fallback).
- Built as one self-contained file, so it also works by just opening `index.html` directly (`file://`).
- Respects reduced-motion preferences for the starfield and effects.

May the Force be with your training.
