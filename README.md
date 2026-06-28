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
- **Progress** — stats, the 30-day saga grid, a detailed **Training log**, the galaxy leaderboard ladder, recent activity, and settings (rename, reset, sound).

### Training log (Progress tab)

Each time you log a day, the game snapshots **exactly which moves you trained and their time / reps for that day**, and lists them in the Progress tab — newest first.

- Tap any gold day in the 30-day saga grid (or any row in the log) to expand it and see the full breakdown.
- The snapshot is stored as it was on the day, so when you rename a move or bump up an interval later (e.g. Wall Sit 30s → 45s once you get stronger), **past days keep their original numbers** — your history is never rewritten.
- Days logged before this feature existed still appear; they just note that no detailed breakdown was saved for them.

## Cross-device sync setup (optional)

Out of the box, your saga is saved on the device you play on. If you want the
**same progress across your phone, tablet and computer**, connect a free
Firebase project and sign in with Google. It takes about five minutes, once.

Your logs are merged additively across devices: a workout logged on *any*
signed-in device is kept everywhere, so nothing gets overwritten — even if one
device was offline while you trained on another.

### Steps

1. Go to the [Firebase console](https://console.firebase.google.com/) and click **Add project**. Give it any name; you can disable Analytics.
2. In the left menu open **Build → Realtime Database → Create Database**. Pick a region, and start in **locked mode** (you'll set rules in step 6).
3. Open **Build → Authentication → Get started**, choose the **Sign-in method** tab, and enable **Google**.
4. Open **Project settings** (the gear icon) → **General** → scroll to **Your apps** → click the web icon **`</>`** to register a web app. Copy the `firebaseConfig` object it shows you.
5. Open `index.html`, search for **`FIREBASE_CONFIG`** near the top of the script, and paste your values in:
   ```js
   const FIREBASE_CONFIG = {
     apiKey: "AIza…",
     authDomain: "your-app.firebaseapp.com",
     databaseURL: "https://your-app-default-rtdb.firebaseio.com",
     projectId: "your-app",
     appId: "1:…:web:…"
   };
   ```
6. Back in **Realtime Database → Rules**, paste this so each person can only read/write their own save, then **Publish**:
   ```json
   {
     "rules": {
       "users": {
         "$uid": {
           ".read": "$uid === auth.uid",
           ".write": "$uid === auth.uid"
         }
       }
     }
   }
   ```
7. In **Authentication → Settings → Authorized domains**, click **Add domain** and add your GitHub Pages domain (e.g. `billychristopher839-dev.github.io`). `localhost` is already allowed for testing.
8. Commit, deploy, then open the published site and use **Progress → Cross-device sync → Sign in with Google** on each device.

### Notes on sync

- The API key in the config is **safe to embed** — it only identifies your project. The security rules in step 6 are what actually protect your data.
- The free **Spark** plan (1 GB storage, generous bandwidth) is far more than this needs.
- Sign-in needs the **published web address** (https). It won't run from a file opened directly off disk (`file://`) — that's expected; the app still works there, just without sync.
- On Safari, if the sign-in popup is blocked it automatically falls back to a full-page redirect.
- If Firebase is left unconfigured or can't load (offline), the game runs exactly as before from local storage.

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
