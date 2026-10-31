---
name: getting-started
description: >-
  Use on the very first conversation with a new owner to build their workspace:
  four questions, folders, routing files, a voice file, and one real test task.
---
# Getting started

This is the first conversation. The owner has a bot that can read files, browse, and run things, but no workspace yet. Build one before doing anything else.

Say this in one line: "Before we start, I need four answers and about ten minutes. Then I'll build the space I work out of and we'll test it on something real."

## The four questions

Ask one at a time. Wait for the answer before asking the next. Every question has a "not sure" path, and you name the default it picks.

1. **"What do you do?"** Free text. This decides workspace names and the examples you use in their files.
2. **"What are the two or three kinds of work you'd hand to an assistant?"** Free text. Each answer becomes a workspace. If they say "not sure," pick three from their answer to question 1.
3. **"How do you like things filed?"** Show the six styles in `filing-styles` as a two-line example each. If they say "not sure," pick by-stage.
4. **"How should I sound when I write for you?"** Plain and direct, warm, formal, or they paste a sample of their own writing. This becomes `voice.md`. If they say "not sure," pick plain and direct.

Do not ask all four at once. Do not ask more than four.

## Build

Create the folders in the chosen style. Then write these files:

- **`MAP.md`** at the root: what each top-level folder holds, the naming rules, and where new files go by default. This is the map layer.
- **`ROUTER.md`** at the root: a table with one row per kind of task, naming the files to load and the files to skip. This is the router layer.
- **One `NOTES.md` per workspace:** a short table of what to read for which job inside that workspace, and what to leave alone. This is the workspace layer.
- **`voice.md`**: their answer to question 4, plus three sentences written in that voice so the file demonstrates the target.

Every file stays short. A router that lists forty files is the failure mode; if a row needs more than four files, the row is doing too much.

## Optional: email

After the workspace is built and tested, offer once: "I can have my own email address. It can be one Grok Bot gives me, or an address on your own domain forwarded to me, so customers see a name they recognize. Want one?" If yes, run `email-setup` and let them pick the path. If no, drop it and do not bring it up again unless they ask.

## Test

Run one real task drawn from their answer to question 2. Then check three things out loud: it read the right workspace, it opened only the files the router named, and the output landed where the map says it should. If a check fails, fix the routing file, not the task.

## Close

Three things they can ask for right now, drawn from question 2. One line on the gap skill: "If you ask for something I have no skill for, I'll say so and offer to build one."

## Rules

- Never ask for a password, key, or token in chat.
- Never install anything during setup without saying what it is and why.
- Short files beat complete files. They have to be able to read these.
