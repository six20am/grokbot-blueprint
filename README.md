# Grok Bot Blueprint

A base workspace for a Grok Bot, built the way the Workspace Blueprint is built: the bot sets itself up on the first conversation, then works out of the space it made.

No file editing. Four questions, one filing style, ten minutes.

**Status:** built. The skills are written and the setup conversation is specified. Not yet run with a new owner on a clean import.

The design is `docs/design.md`.

## What you get

- A workspace in one of six filing styles: military, by stage, by client or project, PARA, numbered index, or by date.
- Three routing layers: a map at the root, a router at the root, and a notes file inside each workspace, so the bot loads only what a task needs.
- A voice file, so anything written for the owner sounds like the owner.
- A gap-finder, so a task with no skill gets a one-line offer to build one, find a tool, or do it by hand, and the gap gets logged.
- A voice extractor, a workspace audit, and a tool-vetting checklist.

## How it works

1. Import the template as a new bot in Grok Bot.
2. The first conversation runs `getting-started`: four questions, one at a time.
3. The bot builds the folders, writes the three routing layers and `voice.md`, then proves it on one real task.

There is no installer and nothing to download. The bot's own computer is the machine.

## Built from

The Workspace Blueprint (`six20am/workspace-blueprint`), which does the same job for Claude Code on a personal computer with a double-click installer. This repo keeps the method and drops the installer, because a Grok Bot already has a computer and a shell.

## Maintained by

Six20AM.
