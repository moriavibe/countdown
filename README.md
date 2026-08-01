# 🕹️ מבצע: סוף שנה · End-of-Year Grading Countdown

A live, retro-arcade dashboard that counts down the last grading pile of the 2025/2026 academic year: three courses, 31 submissions, one very determined lecturer.

**Live dashboard:** https://YOUR-USERNAME.github.io/countdown/ *(replace with your link)*

Friends open the link and watch the numbers drop in real time. No installs, no refreshing needed, and a built-in arcade for anyone who gets stressed just from watching.

## What's inside

- **Live countdown** of submissions left to grade across three courses, with per-course progress bars and deadline chips
- **Stress-o-meter**: a neon gauge that slides from "on the edge" to "vacation mode" as the pile shrinks
- **Deadline timers** ticking down to August 4 and August 21, 2026
- **Retro pinball machine**: canvas-based, with flippers (arrow keys / space / touch), bumpers, and a high score
- **Bubble wrap**: 63 poppable bubbles with proper pop sounds
- **Guided 4-7-8 breathing** for a one-minute reset
- Confetti celebrations, retro sound effects (with a mute toggle), and encouraging messages in Hebrew

## How it works

The whole thing is a single static `index.html`, hosted free on GitHub Pages. There is no build step and no server code in this repo.

The live numbers come from a small **Firebase Realtime Database**. Every open copy of the page holds a live connection to it, so when a value changes, every screen updates within about a second.

Three viewing modes:

- **Viewer** (everyone): sees live data; the big button fires confetti and encouragement only
- **Admin** (the project owner, via Google sign-in): the same buttons actually write to the database
- **Offline fallback**: if the database is unreachable, the page still renders with baseline numbers

Writes are protected by Firebase security rules that allow only the owner's Google account to change data. The Firebase config keys visible in the page source are public by design; the rules are the lock.

## Updating

- **Numbers:** sign in through the crown button in the footer and click away. No file changes needed, ever.
- **Design or features:** edit `index.html` and re-upload it here (Add file → Upload files → Commit). The file name must stay `index.html`. GitHub Pages republishes automatically within a minute or two.

## Tech notes

- Vanilla HTML/CSS/JS, right-to-left Hebrew UI, mobile friendly
- Canvas 2D for the pinball physics and confetti, Web Audio API for the retro sounds
- Firebase JS SDK (ESM from CDN): Realtime Database + Google authentication
- Fonts: Press Start 2P for digits, Heebo for Hebrew

Built with love, caffeine, and a bit of pressure, together with Claude. 💛
