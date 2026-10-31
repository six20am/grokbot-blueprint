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
| `text-messaging` | Picks a phone number with the owner, explains A2P 10DLC before they commit, and sets the rules for quiet hours, opt-in, and sends on an approval card. |

## The four questions

1. "What do you do?" Free text. Decides workspace names and the examples in the files.
2. "What are the two or three kinds of work you would hand to an assistant?" Free text. Each answer becomes a workspace. "Not sure" picks three from answer 1.
3. "How do you like things filed?" The six styles, two-line example each. "Not sure" picks by-stage.
4. "How should I sound when I write for you?" Plain and direct, warm, formal, or a pasted sample. Becomes `voice.md`. "Not sure" picks plain and direct.

## Email

Two paths, because the owner's situation differs.

**Product domain.** Grok Bot gives every bot an address natively. No domain, no mail host, no third-party mailbox. This is the zero-setup path and the default to offer first.

**Their own domain.** The owner forwards an address they own into the bot's Grok Bot inbox. It costs them a provider screen and a verification click, and in exchange the address is one their customers recognize. The skill walks the provider's own screens by name: Google Workspace recipients and routing, Microsoft 365 mail flow rules, Cloudflare Email Routing, Fastmail rules, and host-panel forwarders.

What forwarding does not give them: the ability to reply as that address. That is a separate connection to their mailbox, and the skill says so rather than letting them discover it later.

**Relaying to the owner.** A routine with an email trigger reads new mail and sends the owner a copy. There is no server-side forward switch, so this is the honest substitute, and the skill names its two limits: attachments may be summarized, and it only sees mail after it is saved.

The offer comes once, at the end of `getting-started`, after the workspace is built and tested, in the same question as texting. Declining is final until the owner asks.

## Texting

There is no texting switch on a Grok Bot, and no version of one is coming. Texting needs a phone number, and a number belongs to a carrier, a VoIP service, or a messaging platform. So the skill does not pretend a setting exists; it helps the owner pick a provider and connects it.

**The constraint that decides everything: A2P 10DLC.** US carriers treat software-sent SMS as application-to-person traffic, and application-to-person traffic on a ten-digit number has to be registered: a brand registration for the business, a campaign registration describing the messages, a one-time fee, a monthly campaign fee, and a per-message carrier surcharge. Approval takes days and can be rejected. Every provider walks the owner through it and some cover small volumes under their own registration, but nobody skips it. The skill says this before the owner picks, because it is the reason the cheapest option is often not the right one.

**Three paths.**

| Path | For | Names |
|---|---|---|
| A number they already pay for | An owner with a business phone system already texting customers | Quo (formerly OpenPhone), RingCentral, Dialpad, HighLevel |
| An identity built for an agent | An owner with no phone system, or one who wants the bot's line kept separate | Inkbox |
| A carrier API | A technical owner, or one sending volume and wanting one provider for voice, SMS and email | Twilio, Sinch |

Path A is the default to ask about first, because it needs no new number and the registration is already done. The skill's single qualifying question is whether they already text customers from a business number.

**Costs are stated as shapes, not quotes.** Path A runs to a per-user subscription in the low tens of dollars a month with roughly a cent a message. Path B is a monthly fee for a dedicated number with a few hundred messages included. Path C is a dollar or two a month to hold a number and under a cent a message, plus the registration fees and the owner's own time. The skill tells the bot to confirm current numbers with the provider rather than quote a stale figure.

**The rules once it works.** Every send to a real person goes out on an approval card, the same as email. No marketing texts before 8am or after 9pm in the recipient's own time zone. `STOP` is honored immediately. Marketing and support traffic stay in separate registered campaigns. Cold outreach and purchased lists are out.

## Out of scope

- A per-trade tool subset at setup.
- Reorganizing folders the owner already has. The layers go on top of the existing structure.
- Anything that installs software. A Grok Bot's tools are managed by the app, not by a template.

## Risks

- **The four questions are the whole product.** A bot that asks them badly produces a workspace nobody uses. The skill spells out the order, the defaults, and the ban on asking all four at once.
- **Short files get longer.** Every routing file is supposed to stay small. `workspace-audit` exists to catch the drift, and the router rule is explicit: more than four files in a row means the row is doing too much.
- **Texting costs money in a way email does not.** Two of the three paths carry a monthly fee and a registration that takes days, so the skill leads with cost and the registration requirement instead of letting the owner discover them at checkout. A template that quietly implies a free toggle would be worse than one that says no.
- **The template and this repo can drift.** They are packed from the same text today. The check is a diff of the skill bodies, and it is manual.
