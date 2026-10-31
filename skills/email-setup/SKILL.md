---
name: email-setup
description: >-
  Use when the owner wants the bot to have an email address, on the product
  domain or forwarded from their own domain, or asks whether it can send,
  receive, or forward mail.
---
# Email

Run this when the owner wants you to have an email address, asks whether you can send or receive mail, or wants mail from their own domain to reach you.

There are two ways to give the bot an address. Ask which one they want rather than assuming.

## Path A: an address Grok Bot gives you

On the product domain, natively. No domain, no Cloudflare, no mail host, no third-party signup. Claim it in the app; it is live immediately.

1. Ask what they want before the @, suggesting two or three based on their work. Never pick one silently: a claim is permanent.
2. Check availability first and report what is actually free. Do not claim a name just to test it.
3. Claim the one they pick. One address per bot; if one already exists, use it and say so.

Anything after a plus sign is a tag: `name+shop@` arrives tagged, so a different tagged address per signup shows which service a message came from.

## Path B: their own domain, forwarded to you

They own a domain, so the address can be one their customers would recognize. Forwarding is the setup: mail sent to that address is copied to the bot's Grok Bot inbox, which is the box the bot actually reads.

Walk them through it once, in their mail provider's words, not in generic DNS talk:

1. Claim the Grok Bot address first (Path A). It is the destination, so it has to exist.
2. Go to the domain's mail provider and find where addresses or routing live. Say the common names: Google Workspace "Recipients" or "Routing", Microsoft 365 "Mail flow rules" and "Connected accounts", Cloudflare Email Routing, Fastmail "Rules", and a host panel's "Forwarders" section.
3. Create the address, for example `assistant@theirdomain.com`.
4. Add a forwarding rule from that address to the Grok Bot inbox. On Cloudflare Email Routing it is a route plus a destination address that has to be verified by clicking a link sent to the Grok Bot inbox. Tell them to expect that verification email and that the bot can read the link out to them.
5. Keep a copy at the original address if they want their own archive, or do not, and say which they chose.
6. Send one test message from their own phone, then confirm the bot can read it and say what arrived.

Be honest about what forwarding does and does not give you: you read the copies. Replying from `assistant@theirdomain.com` means sending through their mail provider, which is a separate setup (an app password or an OAuth connection to that mailbox), not something forwarding turns on. If they want the bot to reply as that address, say so plainly and set that up as its own step.

## Forwarding to the owner

Separately from either path, the owner may want mail the bot receives relayed to *their* inbox. There is no server-side switch for that on a Grok Bot inbox, so it is a routine:

1. Create a routine with an email trigger on the bot's address. It fires when mail arrives.
2. Its saved instruction: read the new message, then send the owner a copy at their own address with the sender, subject, and body, and flag anything that looks like a bill, a deadline, or a sign-in link.
3. Confirm the owner's address before saving, and say plainly this is the bot relaying mail, not the mailbox forwarding it.

State two limits out loud: attachments may arrive summarized rather than whole, and the relay only sees mail that arrives after it is saved.

## Sending

Mail goes out as the owner on a card they press Send on. Never send without that card, except a send the owner explicitly asked for and exempted. Reply from the same inbox the message arrived at.

## What not to use it for

Cold outreach, newsletters, and the same message to many people. The approval card carries no unsubscribe link, and that is not mail the owner should send from their own address anyway.

## Say this plainly

The owner should know where the address lives and how to get rid of it before using it for signups. If it can be released, say how. If it cannot, say it is theirs to keep.
