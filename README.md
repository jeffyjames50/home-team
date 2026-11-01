# Home Team

A shared household board for two people: tasks and chores with points, a Jira-style board (To do / In progress / Done), a leaderboard, kudos that add bonus points, emoji reactions, a shopping list and notes.

It works in any browser on any phone or laptop. Nobody needs an account: you open your household once with its invite link or code, and that browser remembers it.

## Features
- **Board**: tasks and chores with points, assignee, due date, and daily or weekly repeats. Status moves To do → In progress → Done.
- **Points and leaderboard**: a finished task gives its points to the person it's assigned to, or to whoever marks it done when it's for anyone. Totals for this week, this month and all time.
- **Appreciation wall**: notes that unlock on their own for point milestones, MVP of the week, streaks and kudos.
- **Kudos**: thank each other and add +5 to +50 bonus points.
- **Reactions**: 😘 🤗 ❤️ 😂 👏 🔥 😮 🥺 🙄 😠 on finished tasks, notes, kudos and leaderboard entries.
- **Shopping list** and **notes**, shared live.
- **Invite link, backup and restore** under *Manage people*.

## Tech stack
- `index.html`: plain HTML, CSS and JavaScript (an ES module), with no framework and no build step.
- **Firebase Cloud Firestore** for realtime shared data, with an offline cache. Loaded from Google's CDN.
- Google Fonts (Unbounded and Manrope), inline SVG artwork, and Canvas confetti.
- Hosted on **Netlify** from this repo (`netlify.toml`). Every push to `main` deploys automatically. `manifest.webmanifest` and the icons let you add it to a phone's home screen.
- `claude-artifact/home-team.html` is the earlier version that runs as a Claude artifact.

## How access works
Each household gets a random 24-character code (about 120 bits), and its data lives under `households/<code>/…` in Firestore. `firestore.rules` stops anyone from listing households, so only someone who has the code or the invite link can reach a household. Treat the invite link like a house key.

## Setup (one time)
1. Create a Firebase project at https://console.firebase.google.com. Google Analytics isn't needed.
2. Go to **Build → Firestore Database → Create database**, choose a location near you, and start in **production mode**.
3. On the **Rules** tab, paste the contents of `firestore.rules`, then click **Publish**.
4. Go to **Project settings → Your apps → Web (`</>`)**, register an app called "Home Team" (Firebase Hosting isn't needed), and copy the `firebaseConfig` values into `config.js`.
5. On https://app.netlify.com, choose **Add new site → Import an existing project → GitHub → home-team**. Leave the build command empty, set the publish directory to `.`, and click **Deploy**. Rename the site under **Site configuration → Change site name**.
6. Open the site, choose **Create your household** (or **Import a backup file**), then send the invite link from **Manage people** to your partner.

## Run locally
```bash
python -m http.server 8765
```
Then open http://localhost:8765.
