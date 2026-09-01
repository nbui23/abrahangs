# Abrahangs

Single-page timer for Emil Abrahamsson's daily hangboard routine, following the
set order and timing of his
[10 Minute Daily Hangboard Routine (FOLLOW ALONG)](https://www.youtube.com/watch?v=3FNZdixeuZw).
One file, no build, no dependencies, no network — open `index.html` and it works.

## The routine

Twice a day, at least 6 hours apart and 6 hours clear of climbing. Every set is
**10 s on, 20 s off**. Feet stay on the floor — "no hangs".

| # | Grip | Sets | Load |
|---|------|------|------|
| 1 | Half crimp, 20 mm edge | 6 × 10 s | ~40% of max |
| 2 | Three-finger drag | 6 × 10 s | ~40% of max |
| 3 | Front 2-finger drag (index + middle) | 2 × 10 s | ~40% of max |
| 4 | Middle 2-finger drag (middle + ring) | 2 × 10 s | ~40% of max |
| 5 | Front 2-finger crimp (index + middle) | 2 × 10 s | ~25% |
| 6 | Middle 2-finger crimp (middle + ring) | 2 × 10 s | ~25% |

20 sets, ~9:50 end to end, after a 10 s "get ready" lead-in that speaks the
first grip so your hands are on the edge before the hang starts. Set counts
come from the video's chapter lengths at 30 s per set — denser
than the write-ups of Emil's original 30-day experiment (10 sets, 50 s rest).
Hang, rest and lead-in seconds are all editable in Settings.

## Setting the load

Percentages are of your **max hang total** — bodyweight plus the weight you can
add for a 5 s max hang on a 20 mm edge — not of bodyweight. Pull that fraction
through your fingers; standing on a bathroom scale, the scale reads the rest of
you.

Emil's worked example: 80 kg bodyweight + 80 kg added = 160 kg total; 40% is
64 kg, so the scale should read 15–25 kg. The two-finger crimps are his weakest
grip and he unloads far less there — scale around 40–45 kg, the ~25% default.
It should feel like light strain, never hard.

## Hosting it free

Any static host will do — it's one file. GitHub Pages, from this directory:

```sh
gh repo create abrahangs --public --source=. --push
gh api -X POST repos/:owner/abrahangs/pages -f 'source[branch]=main' -f 'source[path]=/'
```

To try it on the phone first: `python3 -m http.server 8000` here, then open
`http://<lan-ip>:8000`.

## On the iPhone

- Share → **Add to Home Screen** for fullscreen with no Safari chrome.
- The **silent switch mutes the beeps** — ringer on, or keep the spoken cues
  (speech synthesis ignores the switch).
- Screen Wake Lock holds the display on, and re-acquires when you return to the tab.
- Settings, streak and history live in `localStorage` — per-device, and gone if
  you clear Safari's site data.

## Self-check

Open `index.html?test` — asserts on the set sequence, chapter order, load
arithmetic against Emil's example, and the streak counter, in place of the app.

## Sources

- [10 Minute Daily Hangboard Routine (FOLLOW ALONG)](https://www.youtube.com/watch?v=3FNZdixeuZw) — set order, timing, and the loading clarification in the description
- [Hangboard Training 2 Times Per Day For 30 Days](https://www.youtube.com/watch?v=sBTI9qiH4UE) — the original experiment
