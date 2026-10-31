# Grok Bot Blueprint: Design

**Date:** 2026-10-31
**Status:** built. Skills written and the setup conversation specified. Not yet run with a new owner on a clean import.
**Product:** the public Grok Bot template "Workspace Blueprint", mirrored in this repo.

## What this is

A base workspace for a Grok Bot, set up by the bot itself on the first conversation. The owner answers four questions, the bot builds the folders in the filing style they picked, writes the routing files an AI needs, and tests one real task end to end.

It is the Workspace Blueprint, rebuilt for a machine that already exists. The original installs tools and Claude Code from a double-click script, because a person's own computer starts empty. A Grok Bot starts with a computer, a shell, and a browser, so the installer has nothing to do. What is left is the part that mattered: the four questions, the six filing styles, the three routing layers, and the gap skill.

## Who it is for

Anyone. The setup does not assume a trade. The four questions decide what gets built.

## Decisions made

| Decision | Choice | Rejected |
|---|---|---|
| Front door | The template's first conversation. The bot runs `getting-started` and asks. | An installer script. There is no install to do. |
| Split of work | The bot does all of it: questions, folders, files, test task. | A script for some of it, the bot for the rest |
| Setup questions | Four, one at a time, each with a "not sure" default | Three (too much guessing); eight or more (people quit) |
| Routing file names | `MAP.md`, `ROUTER.md`, `NOTES.md`, `voice.md` | `CLAUDE.md` and `CONTEXT.md`. Those name one product; a Grok Bot is not that product. |
| Filing styles | The same six, with the same defaults | A new set. The six were tested. |
| Gap handling | A skill that asks before building, every time, and logs each gap | Build silently; never build |
| Distribution | Grok Bot template plus this repo as the readable source | Repo only; template only |
| Source of truth | This repo. The template is packed from the same skill text. | Edit the template by hand and let the repo drift |

## What the owner ends up with

```
workspace/
|-- MAP.md              what lives where, naming rules, default placement
|-- ROUTER.md           one row per kind of task: what to load, what to skip
|-- voice.md            how writing should sound, with examples
|-- gap-log.md          one line per task that had no skill
|-- <workspace-1>/
|   |-- NOTES.md        what to read for the work that happens here
|   `-- ...
`-- <workspace-2>/
    |-- NOTES.md
    `-- ...
```

The folder names come from the chosen style. The three routing layers and the voice file are the same under every style.

## The skills

| Skill | Job |
|---|---|
| `getting-started` | The first conversation. Four questions, build, test, close. |
| `filing-styles` | The six styles, with a sample tree each, and the rule that the three layers survive all of them. |
| `gap-finder` | A task with no skill gets one line and three choices, a three-strikes check on the log, and one appended line. |
| `voice-extractor` | Builds `voice.md` from real samples of the owner's writing, and checks it by asking which paragraph is theirs. |
| `workspace-audit` | Checks the map, the routers and the notes against what is actually on disk, and reports the drift. |
| `tool-vetting` | Six questions before recommending anything gets installed or connected, then adopt, try, or skip. |
| `email-setup` | Claims the bot its own address, explains plus-tagging, and sets the rule that mail goes out on an approval card. |

## The four questions

1. "What do you do?" Free text. Decides workspace names and the examples in the files.
2. "What are the two or three kinds of work you would hand to an assistant?" Free text. Each answer becomes a workspace. "Not sure" picks three from answer 1.
3. "How do you like things filed?" The six styles, two-line example each. "Not sure" picks by-stage.
4. "How should I sound when I write for you?" Plain and direct, warm, formal, or a pasted sample. Becomes `voice.md`. "Not sure" picks plain and direct.

## Email

Grok Bot gives every bot an address on the product domain, natively. There is no Cloudflare step, no custom domain, and no third-party mailbox, so this belongs in the template as a claim flow rather than an integration.

The offer comes once, at the end of `getting-started`, after the workspace is built and tested. Declining is final until the owner asks.

## Out of scope

- A per-trade tool subset at setup.
- Reorganizing folders the owner already has. The layers go on top of the existing structure.
- Anything that installs software. A Grok Bot's tools are managed by the app, not by a template.

## Risks

- **The four questions are the whole product.** A bot that asks them badly produces a workspace nobody uses. The skill spells out the order, the defaults, and the ban on asking all four at once.
- **Short files get longer.** Every routing file is supposed to stay small. `workspace-audit` exists to catch the drift, and the router rule is explicit: more than four files in a row means the row is doing too much.
- **The template and this repo can drift.** They are packed from the same text today. The check is a diff of the skill bodies, and it is manual.
