# Home Team

A shared household board for two people: tasks and chores with points, a Jira-style board (To do / In progress / Done), a leaderboard, kudos that add bonus points, emoji reactions, a shopping list and notes.

Live app (Claude artifact): https://claude.ai/artifact/MJtQLjKBsWmQa3TX8emnSz

## Features
- **Board**: tasks and chores with points, assignee, due date, and daily or weekly repeats. Status moves To do → In progress → Done.
- **Points and leaderboard**: a finished task gives its points to the person it's assigned to, or to whoever marks it done when it's for anyone. Totals for this week, this month and all time.
- **Appreciation wall**: notes that unlock on their own for point milestones, MVP of the week, streaks and kudos.
- **Kudos**: thank each other and add +5 to +50 bonus points.
- **Reactions**: 😘 🤗 ❤️ 😂 👏 🔥 😮 🥺 🙄 😠 on finished tasks, notes, kudos and leaderboard entries.
- **Shopping list** and **notes**, shared live between both of you.

## Tech stack
- One `index.html` file: plain HTML, CSS and JavaScript, with no framework and no build step.
- Fonts from Google Fonts: Unbounded for headings, Manrope for body text.
- All artwork is inline SVG; the confetti is drawn on a Canvas.
- Data lives in the Claude artifact database (`window.claude.use("db")`), a realtime document store. Changes sync live through `onSnapshot`.
- Opened outside Claude (for example straight from this repo), the app falls back to `localStorage`, so data stays on that one device.

## Run locally
Open `index.html` in a browser. It runs in local, unsynced mode.
