# 🕹️ מבצע: סוף שנה · End-of-Year Grading Countdown

A live, retro-arcade dashboard that counts down the last grading pile of the 2025/2026 academic year: three courses, 31 submissions, one very determined lecturer.

**Live dashboard:** https://moriavibe.github.io/countdown/ *(replace with your link)*

Friends open the link and watch the numbers drop in real time. No installs, no refreshing needed, and a built-in arcade for anyone who gets stressed just from watching.

## What's inside

- **Live countdown** of submissions left to grade across three courses, with per-course progress bars — deadline-date-forward, so the date reads before the course name
- **Stress-o-meter**: a neon gauge that slides from "on the edge" to "vacation mode" as the pile shrinks
- **Deadline timers** ticking down to August 4 and August 21, 2026
- **Send support**: one button lets visitors cheer Moria on — it fires confetti for them and pings her on Slack
- **Retro pinball machine**: canvas-based, with flippers (arrow keys / space / touch), bumpers, and a high score
- **Bubble wrap**: 63 poppable bubbles with a juicy, satisfying pop sound
- **Guided 4-7-8 breathing** for a one-minute reset, with gentle beach-wave ambience while it runs
- Confetti celebrations, sound effects (with a mute toggle), and encouraging messages in Hebrew

## How it works

The whole thing is a single static `index.html`, hosted free on GitHub Pages. There is no build step and no server code in this repo.

The live numbers come from a small **Firebase Realtime Database**. Every open copy of the page holds a live connection to it, so when a value changes, every screen updates within about a second.

Two roles:

- **Visitors** (everyone): see live, read-only numbers. Their one action is the **Send support** button — it throws confetti and sends Moria a Slack ping. Visitors can never change the counter.
- **Admin** (Moria, via Google sign-in): each course card gains `+` / `−` controls that write to the database. An "edit mode" banner confirms she's signed in.
- **Offline fallback**: if the database is unreachable, the page still renders with baseline numbers, and the support button still pings Slack.

Writes are protected by Firebase security rules that allow only the owner's Google account to change the counter. The Firebase config keys visible in the page source are public by design; the rules are the lock.

### Support button (Slack)

The support button posts to a **Slack Incoming Webhook** straight from the browser. To turn it on, create a webhook for the channel you want and paste its URL into the `SLACK_WEBHOOK` constant near the top of the main script in `index.html`. Until it's set, the button still fires confetti and thanks the visitor — it just doesn't send the ping. The webhook URL lives in the page source, so use one scoped to a channel you don't mind being writable.

## Updating

- **Numbers:** sign in through the crown button in the footer and use the `+` / `−` controls on each course card. No file changes needed, ever.
- **Design or features:** edit `index.html` and re-upload it here (Add file → Upload files → Commit). The file name must stay `index.html`. GitHub Pages republishes automatically within a minute or two.

## Tech notes

- Vanilla HTML/CSS/JS, right-to-left Hebrew UI, mobile friendly
- Canvas 2D for the pinball physics and confetti, Web Audio API for the retro sounds
- Firebase JS SDK (ESM from CDN): Realtime Database + Google authentication
- Support pings via a Slack Incoming Webhook (`SLACK_WEBHOOK` in the page source)
- Font: Rubik (single family, weights 400–900)

Built with love, caffeine, and a bit of pressure, together with Claude. 💛
