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
- An email skill, so the bot can claim its own address and send and receive on the owner's behalf.
- A texting skill, so the bot can pick a phone number with the owner and send real SMS once a provider is connected.

## Email

Two paths, and the owner picks one.

**A Grok Bot address.** The bot claims its own on the product domain. No domain, no Cloudflare, no mail host. Plus-tagged addresses work, so a different tag per signup shows which service a message came from.

**Their own domain.** The owner creates an address such as `assistant@theirdomain.com` at their mail provider and forwards it to the bot's Grok Bot inbox. The skill walks them through the provider's own screens, including the verification email a service like Cloudflare Email Routing sends to the destination address.

Separately, the bot can relay what it receives to the owner's inbox. That is a routine with an email trigger, not a mailbox setting, and the skill says so rather than implying a forward switch exists.

## Texting

There is no texting switch on a Grok Bot and there is not going to be one. A text needs a phone number, and a number belongs to a carrier, a VoIP service, or a messaging platform, so the skill helps the owner pick one and connects it.

**Start with this, because it decides everything else:** US carriers require application-to-person SMS on a ten-digit number to be registered, under a brand and a campaign, with a one-time fee and a monthly one. Approval takes days and can be rejected. Every provider walks you through it. Nobody skips it.

Then three paths, and the skill asks which fits:

- **A number you already pay for.** If you run a business phone system, you probably already text customers from it, and the registration is done. Quo, RingCentral, Dialpad, HighLevel.
- **An identity built for an agent.** No phone system, or you want the bot's line separate from your business one. Inkbox gives an agent a number, a mailbox, and iMessage together.
- **A carrier API.** Technical, or sending volume, or wanting one provider for voice, SMS and email. Twilio and Sinch. Cheapest per message, most setup.

Costs are given as shapes rather than quotes, with a note to confirm current pricing. Every send to a real person goes out on an approval card, quiet hours are respected, and `STOP` is honored immediately.

`skills/text-messaging` covers all of it.

## How it works

1. Import the template as a new bot in Grok Bot.
2. The first conversation runs `getting-started`: four questions, one at a time.
3. The bot builds the folders, writes the three routing layers and `voice.md`, then proves it on one real task.

There is no installer and nothing to download. The bot's own computer is the machine.

## Built from

The Workspace Blueprint (`six20am/workspace-blueprint`), which does the same job for Claude Code on a personal computer with a double-click installer. This repo keeps the method and drops the installer, because a Grok Bot already has a computer and a shell.

## Maintained by

Six20AM.
