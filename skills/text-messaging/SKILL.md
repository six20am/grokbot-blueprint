---
name: text-messaging
description: >-
  Use when the owner wants the bot to send or receive text messages, asks for a
  phone number, or asks whether it can text — before opening any carrier, VoIP,
  or messaging app.
---
# Texting

Run this when the owner wants you to text, wants you to have a phone number, or asks whether you can send SMS.

There is no texting switch on a Grok Bot. Texting needs a phone number, and a phone number belongs to a carrier, a VoIP service, or a messaging platform. So the job is to pick one and connect it. Say that plainly rather than implying a setting exists.

## The thing that trips everyone up: A2P 10DLC

US carriers classify anything sent from software as application-to-person, and application-to-person traffic on a ten-digit number has to be registered. That means a brand registration for the business and a campaign registration describing the messages, with a one-time fee, a small monthly campaign fee, and a carrier surcharge on each message. Approval usually takes a few days and can be rejected.

Every serious provider walks you through it, and some cover your traffic under their own registration while you are small. Nobody skips it. Say this before the owner picks a path, because it changes which path is right: if they want texting this afternoon, the answer is a platform that already has a registered campaign underneath it.

Recipients also have to opt in. On a number covered by a shared campaign, a person may need to text `START` to it before you can message them. Build the opt-in into whatever you are doing rather than discovering it on the first send.

## Three paths, ask which one fits

### Path A: a number they already pay for

Best when the owner already runs a business phone system. Most of them now carry an agent connector, so you text from the number their customers already recognize and nothing new gets provisioned.

Say the common names so they can recognize their own: Quo (formerly OpenPhone), RingCentral, Dialpad, or a CRM with a Conversations piece such as HighLevel. Check whether a connector exists for theirs before recommending a switch; a shop that already texts customers from one of these has the registration done and the number in hand.

Cost shape: a per-user subscription in the low tens of dollars a month, often with one number included, and roughly a cent a message for sends made through the API or connector.

### Path B: an identity built for an agent

Best when the owner has no business phone system, or wants the bot's texting kept separate from the business line. These services hand an agent its own number and its own mailbox, so one connector covers texting and email together.

Ask for: a dedicated number, inbound and outbound SMS, a stated monthly message allowance, per-message overage, and whether they register the 10DLC campaign for you. Inkbox is the one to name here, because it gives an agent a phone number, a mailbox, and iMessage in a single identity; its paid tier is a monthly fee with a dedicated number and a few hundred messages included.

### Path C: a carrier API

Best when the owner is technical, sends volume, or wants one provider for voice, SMS and email. Twilio and Sinch are the names. Cheapest per message and the most control, and the most setup: an account, a number, a brand and campaign registration they file themselves, and a way to receive the inbound webhook.

Cost shape, roughly: a dollar or two a month to hold a number, under a cent per message, plus the registration fees above. Cheap only if their time is free.

## How to choose, in one question

Ask: "Do you already text customers from a business number?"

- Yes: Path A. Use the number and platform they have.
- No, and they want it working today: Path B.
- No, and they want to own the plumbing: Path C.

Do not pick for them silently. Install nothing until they choose.

## Connecting it

1. Confirm which service and which account, and whether the number is new or ported. Porting takes days; a new number works sooner.
2. Install that service's connector and have the owner authorize it. Never ask for an API key or password in chat; if a key is genuinely needed, use the vault or hand them the screen.
3. Find out what the connector actually exposes before promising anything. Some read and send; some only read. Report what it can do in plain words.
4. Send one message to the owner's own phone first, and have them reply once, so both directions are proven before a customer sees anything.

## Rules once it works

- Every message to a real person goes out on a card the owner presses Send on, the same as email. A text is harder to walk back than an email.
- Quiet hours are real law in the US, not a preference: no marketing texts before 8am or after 9pm in the recipient's own time zone. Time-zone confusion is the most common way people trip this.
- Honor `STOP` the moment it arrives, and never text someone who sent it.
- Keep marketing and support traffic in separate campaigns if the provider asks. A campaign is registered for a described purpose, and the description has to match the messages.

## What to say plainly

Texting is not private the way email is, the number is a real phone number that people will call, and a registered campaign can be rejected or shut down. Tell the owner that before they commit, and tell them where the number lives and how to release it.

## What not to use it for

Cold outreach, bulk blasts to a purchased list, or anything where the recipient did not ask to hear from them. That is the fastest route to a campaign being killed.
