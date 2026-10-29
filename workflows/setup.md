# Set Me Up

Make this project mine through a short Q&A. Ask these one at a time, and wait for each answer before asking the next. Keep each question to a sentence or two, with a quick example if it helps.

1. **What's your goal?** Like losing weight, building muscle, getting stronger, or just moving more. A number and a timeframe help if you have them.
2. **Where are you starting from?** Age, height, weight, and how much you've trained before.
3. **Where do you train, and with what?** Home, gym, or both. For home, list the equipment with its weights, like "dumbbells up to 10 kg and a pull-up bar".
4. **How many days a week can you train, and for how long?** And which days work best.
5. **Anything I should know about your health?** Injuries, pain, conditions, or anything a doctor has told you. "Nothing" is fine.
6. **kg or lb? And what language should your plan be in?**

If my setup message already answers some of these, skip them. If my health answer needs a doctor's OK first, follow Safety in [AGENTS.md](../AGENTS.md) before planning anything.

Then, in one go:

* Rewrite [profile.md](../context/profile.md) from my answers to 1, 2, 5, and 6, and [training.md](../context/training.md) from my answers to 3 and 4, under their headings. Drop the example content. Keep both short and specific.
* Clear the example out of [tracker.json](../assets/tracker.json): delete every workout, weight entry, week note, and review. Then set `weightUnit`, `targetWeight` (or `null` if my goal has no target weight), `start`, and `restDays`, as in [maintain.md](maintain.md). If I gave you my weight, log it as the first weight entry, dated today.
* Plan my first four weeks, as in [plan.md](plan.md#plan-four-weeks).
* Tell me it's done in a few sentences: the split, what the first week looks like, and that after each workout I can just tell you how it went. Then tell me to open the tracker to see it.
