---
name: gap-finder
description: >-
  Use when a task has no matching skill or routing row, to offer building one,
  finding a tool, or doing it by hand and log the gap.
---
# Gap finder

Run this when a task arrives that no saved skill covers and no routing row names. Also run it when the owner says "gap finder" or asks what to do about a task you can't do.

## Say so first

One line, no apology paragraph: "I don't have a skill for that. I can build one, find an outside tool, or do it by hand this once." Then offer the three choices.

## Before offering, check the log

Read `gap-log.md`. If the same kind of task has been done by hand three times, say so and recommend building instead of offering a menu. That is the three-strikes rule, and it is the whole point of keeping the log.

## The three choices

**Build.** A short interview, four questions at most: what the task is, what goes in, what comes out, and what must never happen. Then save it as a skill in Grok Bot, with a description that says when to use it, add one row to the right `NOTES.md` or to `ROUTER.md` so it gets found next time, and run the task with the new skill so it is proven, not just written.

**Find.** Search for an outside tool or connector that does the job, and run `tool-vetting` on it. Nothing gets installed without a clear verdict and the owner's yes.

**By hand.** Do the task now.

## Log it

Whichever choice was made, append one line to `gap-log.md`: the date, the task in a few words, and the choice. Write the line with the real date, and never invent one.

## Never

- Build anything without asking first.
- Install anything that hasn't been vetted and approved.
- Rewrite the map or a router while adding a skill. One added row, nothing else.
