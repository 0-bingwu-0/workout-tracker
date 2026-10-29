# Maintain the Tracker

Keeping the tracker up to date means editing its data, not the page. The tracker page is `index.html`, and everything it shows lives in `assets/tracker.json`. Edit the JSON. StashBase shows the change in the tracker within a couple of seconds, even while it's open.

## Record what I tell you

I can tick things off in the tracker myself, but sometimes I'll just tell you, like "Did legs today, squats felt easy" or "72.4 this morning". Record it, and reply in a sentence.

* A workout I finished: mark it and its exercises done. Whatever I said about it goes in its note, added to what's there, in my words.
* My weight: a weight entry for that day.
* Pain: also follow Safety in [AGENTS.md](../AGENTS.md).
* If I don't say which workout, it's the one planned for that day. If that's still a guess, ask.

## Editing rules

* Keep it valid JSON. Change only what you need, and leave every other field as it is, including fields not listed here.
* Dates are `YYYY-MM-DD`. Weeks start on Monday. A week belongs to the month its Thursday is in.
* New ids are unique: workouts `w-<date>` (with `-2` for a second one that day), exercises `e1`, `e2`, and so on within a workout, weight entries `b-<date>`.
* Every weight in the file uses `weightUnit`.
* Don't change `schemaVersion` or `index.html`.

## Top level

| Field | What it holds |
| --- | --- |
| `weightUnit` | `"kg"` or `"lb"`. |
| `targetWeight` | The goal weight, or `null`. The weight chart shows it as a dashed line. |
| `start` | My starting point, shown at the bottom of every plan page: a list of `{ "label", "text" }`. `label` can be empty. Written once at setup, never updated. |
| `restDays` | Seven lines, Monday to Sunday, shown on plan pages for days without a workout, like `"Walk 20–30 min"`. |
| `weekNotes` | Notes for each planned week, keyed by its Monday: `{ "focus", "cardio", "effort", "progression" }`. Shown at the top of the week on its plan page. Any of them can be empty. |
| `workouts` | Every planned and finished workout. |
| `body` | The weight log. |
| `reviews` | Weekly and monthly reviews. |

## Workouts

```json
{ "id": "w-2026-11-02", "title": "Push + Core", "date": "2026-11-02", "type": "A", "duration": 30, "status": "done", "note": "Push-ups felt OK.", "exercises": [
  { "id": "e1", "name": "Push-ups", "sets": 3, "target": "8–10", "done": true }
] }
```

* `type` is `A`, `B`, `C`, `D`, `cardio`, or `other`. The plan page builds the split from the first title of each type, so keep one title per type.
* `status` is `todo`, `doing`, `done`, or `skipped`. When I tick exercises on the page, it moves the status by itself.
* `duration` is in minutes, or `null`.
* `target` is text: a number like `"10"`, or a range like `"8–10"` with an en dash. A time works too, like `"30 s"`.
* Put the weight or variation in `name`, like `"Goblet squats (8 kg)"`. Reviews find exercises by `name`, so use exactly the same name for the same exercise every time.

## Weight log

```json
{ "id": "b-2026-11-08", "date": "2026-11-08", "weight": 72.6, "note": "" }
```

Planned weigh-in days can be added ahead of time with `"weight": null`.

## Reviews

```json
"reviews": {
  "weeks": { "2026-11-02": { "conclusion": "All 4 done. Squats are easy.", "calls": { "Squats": "up" } } },
  "months": { "2026-11": { "summary": "" } }
}
```

* Weeks are keyed by their Monday. `calls` holds only `"up"` (Step up) and `"down"` (Step back). Exercises that stay are left out.
* Months are keyed `YYYY-MM`.

## Size

The tracker holds up to 500 KB and 20,000 values, about three years of training. If it gets close, move the oldest year's workouts and reviews to `assets/archive-<year>.json` and tell me.
