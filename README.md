# Abrahangs

Single-page timer for Emil Abrahamsson's daily hangboard routine, following the
set order and timing of his
[10 Minute Daily Hangboard Routine (FOLLOW ALONG)](https://www.youtube.com/watch?v=3FNZdixeuZw).
One file, no build, no dependencies, no network — open `index.html` and it works.

## The routine it runs

Twice a day, every day, at least 6 hours apart (and 6 hours clear of climbing).
Every set is **10 s on, 20 s off**. Feet stay on the floor — "no hangs".

| # | Grip | Sets | Load |
|---|------|------|------|
| 1 | Half crimp, 20 mm edge | 6 × 10 s | ~40% of max |
| 2 | Three-finger drag | 6 × 10 s | ~40% of max |
| 3 | Front 2-finger drag (index + middle) | 2 × 10 s | ~40% of max |
| 4 | Middle 2-finger drag (middle + ring) | 2 × 10 s | ~40% of max |
| 5 | Front 2-finger crimp (index + middle) | 2 × 10 s | lower — ~25% |
| 6 | Middle 2-finger crimp (middle + ring) | 2 × 10 s | lower — ~25% |

20 sets, 200 s of hanging, ~9:50 end to end. Set counts come straight from the
video's chapter lengths at 30 s per set: the 3-minute chapters are 6 sets, the
1-minute ones 2, and 20 × 30 s lands on the 9:54 of routine left after the
2:00 intro.

Note this is denser than the widely-quoted write-ups of Emil's original 30-day
experiment (10 sets, 50 s rest) — the follow-along video is what's implemented
here. Hang and rest seconds are editable in Settings if you want the older
spacing.

### Setting the load

Percentages are of your **max hang total**, not of bodyweight. Max total =
bodyweight + the weight you can add for a 5 s max hang on a 20 mm edge. Pull
40% of that through your fingers; standing on a bathroom scale, the scale reads
the rest of you.

Emil's own worked example, from the video description: 80 kg bodyweight, ~80 kg
added on a max hang → 160 kg total; 40% is 64 kg, so the scale should read
15–25 kg while he pulls. The two-finger crimps are his weakest grip, and there
he unloads far less — scale around 40–45 kg. That's the ~25% default; both
percentages are editable in Settings. It should feel like light strain, never
hard.

## Hosting it free

GitHub Pages, from this directory:

```sh
git init && git add -A && git commit -m "Abrahangs timer"
gh repo create abrahangs --public --source=. --push
gh api -X POST repos/:owner/abrahangs/pages -f 'source[branch]=main' -f 'source[path]=/'
```

Live a minute later at `https://<user>.github.io/abrahangs/`. Netlify Drop
(drag the folder onto app.netlify.com/drop) and Cloudflare Pages work the same
way — any static host will do, it's one file.

Local test on the phone first: `python3 -m http.server 8000` here, then open
`http://<mac-lan-ip>:8000` on the iPhone.

## On the iPhone

- Share → **Add to Home Screen** for a fullscreen app with no Safari chrome.
- The **silent switch mutes the beeps.** Ringer on, or turn beeps off and keep
  the spoken cues (those are speech synthesis and ignore the switch on iOS).
- Screen Wake Lock keeps the display on while the timer runs; it re-acquires
  when you come back to the tab.
- Settings, streak and history live in `localStorage`, so they're per-device
  and vanish if you clear Safari's site data.

## Self-check

Open `index.html?test` in a browser — asserts on the set sequence, the video's
chapter order, the load arithmetic against Emil's worked example, and the
streak counter render in place of the app.

## Sources

- [Emil Abrahamsson — 10 Minute Daily Hangboard Routine (FOLLOW ALONG)](https://www.youtube.com/watch?v=3FNZdixeuZw) — set order, timing, and the loading clarification in the description
- [Hangboard Training 2 Times Per Day For 30 Days](https://www.youtube.com/watch?v=sBTI9qiH4UE) — the original experiment
