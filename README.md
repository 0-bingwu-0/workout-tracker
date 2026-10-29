# Workout Tracker

A workout plan only helps if it fits you: your goal, the equipment you have, and the days you can actually train. It also has to change as you go. Step up when something gets easy, back off when you're worn out or something hurts. Most apps record what you did. Changing the plan is still up to you.

This project gives you a tracker and a coach. Tell the Agent your goal and what you have to work with, and it plans your workouts in the tracker. After a workout, tell it how it went in a sentence. It checks the workout off and keeps your notes. Each week, it looks at how you did and decides what steps up or back next week.

## Getting started

Open this project in StashBase and tell the Agent:

1. **"Set me up."** It asks you a few questions, one at a time: your goal, where you're starting from, where you train and with what, how many days a week, anything about your health, and kg or lb. Then it writes down your profile and how you train, and plans your first four weeks.
2. **Open `index.html`.** The calendar shows each workout with its exercises. Click one for sets and target reps. Tick ✓ when you're done, or just tell the Agent.
3. **"Did legs today. Squats felt easy, my left knee didn't like the lunges."** It marks the workout done, saves your note, and tells you if anything should change. Your weight works the same way: "72.4 this morning."
4. **"Review my week."** On Sunday, after you weigh in. It looks at what you finished, your notes, and your weight trend, decides which exercises step up or back, writes the week's review, and sets up next week.
5. **"Plan next month."** It plans the next four weeks from how this month went.

When life gets in the way, just say so: "Move Thursday to Friday", "I got a kettlebell", or "I'm traveling, no pull-up bar this week." It changes the plan to fit.

The template comes with an example: a beginner losing weight at home with light dumbbells and a pull-up bar, one week in. Open the tracker to see what you get. Setup replaces the example with yours.

The Agent is a coach, not a doctor. If you have a health condition or an injury, check with a doctor before you start.

## The tracker

* **Calendar and all workouts:** every workout with its exercises, status, and notes. Drag a card to another day to move it.
* **Plans and reviews:** each month's training plan, week by week, and its review, with how many workouts you finished and how your weight moved.
* **Weight:** a chart against your goal weight, and the weight log behind it.
* **Check-ins:** how many workouts you finished, this week, this month, and overall.

Your changes save as you go, and what the Agent records shows up within a couple of seconds. At the end of a month, if nothing needs to change, a button on the plan page copies your last week into every week of next month. When something should change, ask the Agent to plan next month instead.

## Make it yours

Setup covers most of it. You can also change things anytime:

* **Your goal and health** are in `context/profile.md`, and **where you train, your equipment, and your schedule** are in `context/training.md`. Edit them, or just tell the Agent.
* **How the Agent coaches,** like rest between sets and when an exercise steps up, is in `workflows/plan.md`.
* **The Agent's persona and rules** are in `AGENTS.md`.

## Files

Three layers: `context/` is about you, `workflows/` is how the Agent works, and the tracker is where the results go.

* `AGENTS.md`: the Agent's persona, safety rules, and the task index.
* `CLAUDE.md`: points Claude Code to `AGENTS.md`.
* `context/profile.md`: who you are, your goal, your health, and settings like kg or lb.
* `context/training.md`: where you train, your equipment, and your schedule.
* `workflows/setup.md`: the setup Q&A.
* `workflows/plan.md`: how the Agent coaches, plans four weeks at a time, reviews each week, and changes the plan.
* `workflows/maintain.md`: how the Agent records what you tell it, and the format of `tracker.json`.
* `index.html`: the tracker page. It only shows and edits your data.
* `assets/tracker.json`: everything in the tracker: workouts, notes, weight, and reviews.
* `assets/banner.png`: the tracker's banner.
