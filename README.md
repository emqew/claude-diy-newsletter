# Your own AI news digest

A personal newsletter, written by Claude, about *your* field. On the days you choose, it researches what's new, checks every link, writes a short, scannable issue organized around what you're responsible for, and delivers it where you'll actually read it. It also learns from your feedback.

**Setup takes about 5 minutes, and you don't edit anything.** You paste one prompt, answer a few questions, and Claude does the rest.

---

## What you need

- **The Claude desktop app with Cowork.** Scheduled tasks need your computer awake around run time; if it was asleep, the issue still arrives that day, just later.
- **Web search** (on by default).
- **Optional:** a connector for where you want to read it (Slack, monday.com/Asana). Without one, Claude can save issues as files or build you a reader page.

---

## Setup

1. **Copy** the full contents of `newsletter-prompt.md`.
2. **Paste it into a new Claude chat** in Cowork and send it.
3. **Answer the questions.** Four quick rounds: who you are, what you own, sources and style, and when and where. Claude suggests answers for most of them, so you mostly confirm or tweak. "You decide" works too. Work in B2B social? Pick **Marcela's B2B social starter pack** in round two for a ready-made set of topics and sources you can adapt.
4. **Check the summary** and say yes.
5. **Approve the scheduled task.** Claude can also run a test issue right away so you see what you'll get.

That's it.

---

## Delivery options

Claude only offers what your setup supports, simplest first:

| Option | What you get |
|---|---|
| **File** | Each issue saved to a folder. No connectors needed. |
| **Slack DM** | Each issue sent to you in Slack. |
| **Task item** | A monday.com or Asana item per issue, plus a notification. Claude creates the board for you. |
| **Web page** | A nicely styled private page with an archive. Claude builds it for you. |

---

## Changing things later

Just ask Claude in a chat: *"Add a source to my digest"*, *"make Fridays shorter"*, *"skip crypto news"*, *"pause it next week"*. It updates your settings and shows you what changed.

You can also tune it through feedback: leave it where each issue's footer says (it depends on your delivery option) with things like "less X", "more data, fewer opinions". Each run reads your feedback and treats it as a standing rule.

---

## How it thinks

- **It informs, it doesn't decide for you.** Each issue points at signals and open questions for your work; the conclusions are yours.
- **Clear beats clever.** Every item makes sense without clicking: who did what, and why it's worth your time.
- **Fewer, better items.** Two solid stories beat a full issue with one shaky one.

## Built-in safeguards

- **Accuracy:** every link is opened and checked for date and content; opinions and vendor research are labeled as such; nothing is invented.
- **You stay in control:** during setup, Claude asks before creating anything (the scheduled task, a board, a page). Scheduled runs never change their own settings.
- **No surprise actions:** it only does what your delivery method needs, and it never sends email on your behalf.
- **No duplicates:** a re-run on the same day does nothing.
- **Never skips:** quiet days get a one-item issue.
- **Failure fallback:** if delivery fails, the issue is saved as a file and you're told it wasn't delivered.

---

## Rather just read?

This was built by Marcela Quintela, who shares her own B2B social picks as **B2B BnB** (B2B, but not boring). If you'd rather follow along than set up your own, subscribe at [b2bbnb.substack.com](https://b2bbnb.substack.com/).
