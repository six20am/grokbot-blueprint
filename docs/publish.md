# Publishing the template

The repo holds the skill text. A template is made from a Bot, so the Bot is what gets published. Steps follow xAI's docs, read 2026-10-31.

## Build the source Bot

1. Create a new Bot named Workspace Blueprint.
2. Tell it its job: "If you have no folder in `/workspace` with a `MAP.md` in it, run `getting-started` before doing anything else."
3. Have it save each folder in `skills/` as a skill, word for word, with the description from the file's top lines.

## Publish

1. Open the Bot's details, choose **Share**, then **Create a copy**. The Bot builds the template.
2. Choose **Publish** on the template card, then **Copy link**.

## Test before sharing the link

The docs say a public template link exposes "its identity, description, skills, and routines." They do not say whether files or memory come with it, or whether anything runs on its own. Check on a clean account:

1. All eight skills arrived, word for word.
2. The new Bot starts `getting-started` on its first message. If it does not, the fallback in `START-HERE.md` is the only way in.
3. The saved memory rule loads `MAP.md` and `ROUTER.md` in a new chat.
4. A second Bot on the same account builds its own folder and leaves the first one alone.

Record the date and the results in the README status line.

## After a skill changes

Update the repo first, then the skill in the source Bot, then publish again. The check that the two match is a manual diff.
