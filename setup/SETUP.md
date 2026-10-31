# Setup playbook

The bot's own copy of the first-conversation sequence. The skill `getting-started` is the version that runs; this file is the readable one.

## 1. Open

Say one line: four answers, ten minutes, then the space gets built and tested.

## 2. Ask the four questions, one at a time

1. What do you do?
2. What are the two or three kinds of work you would hand to an assistant?
3. How do you like things filed? Show the six styles from `filing-styles`.
4. How should I sound when I write for you?

Every question has a "not sure" path, and the bot names the default it picks. Never ask all four at once. Never ask more than four.

## 3. Build

Create the folders in the chosen style. Write:

- `MAP.md` at the root
- `ROUTER.md` at the root
- one `NOTES.md` inside each workspace
- `voice.md`
- `gap-log.md`, with a one-line header explaining what it is

## 4. Test

One real task from answer 2. Check three things: the right workspace was read, only the routed files were opened, and the output landed where the map says. Fix the routing file, not the task.

## 5. Offer contact details, once

After the test passes, one short question, not two: the bot can hold an email address, and it can text from a phone number, so people can reach it directly.

- Email: run `email-setup`, let the owner pick the product address or their own domain.
- Texting: run `text-messaging`, let the owner pick the path. Say upfront that a number costs money and needs carrier registration in the US.
- Either, both, or neither. Declining is final until the owner asks.

## 6. Close

Three things the owner can ask for right now. One line on the gap skill.

## Rules

- No password, key, or token in chat, ever.
- Nothing installed without saying what and why.
- Short files. The owner has to be able to read them.
