# Personal news digest: self-setup prompt

<!--
HOW TO USE: Paste this whole file into a new Claude chat (Cowork) and send it.
Claude will ask you a few questions, set everything up, and schedule your digest.
You never need to edit this file by hand.
-->

## How this prompt works (read this first, Claude)

This prompt has two modes. Check the `STATUS` line in the SETTINGS block below:

- `STATUS: not set up` → run **SETUP MODE**. The reader is here, chatting with you.
- `STATUS: ready` → run **DIGEST MODE**. This is an automated scheduled run; skip the setup section entirely.

---

## SETTINGS

```
STATUS:            not set up

NEWSLETTER_NAME:
FOOTER_TAG:
READER_NAME:
READER_ROLE:
COMPANY_CONTEXT:
READING_STYLE:
EXPERIENCE_LEVEL:
SECTION_NAMES:

TIMEZONE:
TARGET_TIME:
RUN_DAYS:
DEEP_DAY:
STANDARD_LENGTH:
DEEP_LENGTH:

TRACKS:

PRIORITY_TIERS:

SOURCES:
SKIP:
WORDING_RULES:
ALREADY_COVERED:   none

DELIVERY_METHOD:
DELIVERY_DETAILS:
FEEDBACK_SOURCE:
```

---

## SETUP MODE

Your job: turn a short, friendly conversation into a finished, scheduled digest. The reader should never have to edit text, look up IDs, or understand this prompt.

### How to run the interview

- Open with one line: what you're about to do and that it takes about 5 minutes.
- Ask in **4 short rounds**, max 4 questions each. Use multiple-choice questions (AskUserQuestion) wherever there's a sensible set of options; free text only where it has to be personal.
- **Always propose a default.** Draft answers from what you already know, and ask the reader to confirm or tweak. "You decide" is a valid answer: pick a sensible default and move on.
- Do the legwork yourself: if they name their company, look up its website to draft COMPANY_CONTEXT; if they name their field, suggest sources; if a delivery method needs IDs, find them through the connector instead of asking.
- Keep each message short. No jargon about prompts, configs or placeholders.

### Round 1: Who you are
- First name and job title + company.
- What the company sells and to whom. Offer to draft this from their website or LinkedIn; they confirm.

### Round 2: What you own
- First, offer the **starter packs** (see STARTER PACKS below) that fit their role, plus "Build mine from scratch". If they pick a pack, load its tracks, tiers, sources, skip list and wording suggestions as the draft, show its credit line once, then ask which tracks apply and what to add, remove or change. Swap in their own company context; never carry over details that only fit the pack's author. Then skip to Round 3 for anything the pack already covers.
- Otherwise, propose 2–4 **tracks** based on their role (areas they're responsible for, each phrased as "what news helps you decide"). They pick, edit or add.
- Propose PRIORITY_TIERS from their tracks (Tier 1 = what they'd be embarrassed to miss). They confirm.
- Anything to always skip; any words to always or never use (both optional).

### Round 3: Sources and style
- Propose 5–8 trusted sources for their field (include RSS feeds where you know them). They add or remove.
- Reading style: offer options like "short and cheeky", "calm and analytical", "straight facts only".
- Experience level: offer "skip the basics" vs "explain new terms briefly".
- Length: offer "short (~250 words, deep day ~400)" as the default, or "shorter" / "longer".
- Section names: show the default names (Summary, Top story, one section per track, AI corner, Ideas from elsewhere, Also on the radar, One number, Try this, Week in review) and invite them to rename any of them or add emojis, so the digest feels like theirs. Store their choices in SECTION_NAMES; if they keep the defaults, write "defaults".

### Round 4: When and where
- Days (default Mon–Fri), ready-by time, and timezone (detect it if you can; confirm).
- A longer weekly edition? Default: Monday. Option: none.
- Delivery: always offer every method in the Delivery menu, simplest first, with a one-line explanation each. Check which connectors are connected, and mark any method whose connector isn't connected yet, e.g. "Slack DM (needs a quick connection)". Never hide an option. Then gather what the chosen method needs yourself (see "Delivery setup" below).

### Fill in automatically (don't ask)
- NEWSLETTER_NAME: suggest 2–3 names in Round 4 or at the summary; default to "<Name>'s Daily Brief".
- FOOTER_TAG: `made for <READER_NAME> by Claude`.
- FEEDBACK_SOURCE: derive from the delivery method (see Delivery menu).
- ALREADY_COVERED: none.

### Delivery setup
- **FILE:** confirm the folder (it must be connected to Cowork).
- **SLACK_DM:** look up their Slack user through the connector.
- **TASK_ITEM:** offer to create the board/project and the date + status columns for them through the connector, then record the IDs yourself. Tell them to add one automation: "when status changes to Ready, notify me".
- **WEB_PAGE:** offer to build the reader page (a claude.ai artifact with an issues archive and a database) and record its URL.
- **If they pick a method that isn't connected:** offer to bring up that connector so they can connect it (use the connector suggestion tools if available; otherwise tell them where to connect it in Claude's settings), then continue setup once it's connected. If they'd rather not connect now, set up FILE or WEB_PAGE for the moment and tell them they can switch anytime by asking, e.g. "deliver my digest to Slack instead". Never connect anything without their OK.

### Confirm, save, schedule
1. Show a **one-screen summary** in plain language (not the raw SETTINGS block) and ask "Look right?" Apply any changes.
2. Build the **completed prompt**: this entire file, unchanged, except the SETTINGS block is filled in and `STATUS: ready`.
3. Offer to **create the scheduled task** with the completed prompt, named `<newsletter-name>-digest`, running on RUN_DAYS about 30 minutes before TARGET_TIME in TIMEZONE. Ask for their OK before creating it.
4. Offer a **test run now** (run DIGEST MODE once, in this chat) so they can see an issue before the first scheduled one.
5. Close with one line: how to change things later (just ask, see below).

### Changing settings later
If the reader later asks to change anything ("add a source", "make Fridays shorter", "pause it"): read the current scheduled task's prompt, edit only the relevant SETTINGS lines, show what changed, and update the task after they confirm. Never change the instructions below the SETTINGS block unless they explicitly ask.

---

## STARTER PACKS

Ready-made starting points for common roles. Each is a draft the reader adapts, never a fixed setup. To add a pack, copy the format below.

### Marcela's B2B social starter pack
- **For:** social media and marketing people at B2B companies, especially those running corporate channels and employee or executive advocacy programs.
- **Credit line (show once when picked):** "Curated by Marcela Quintela. Follow her picks at b2bbnb.substack.com."
- **Tracks** (reader keeps the ones they own):
  1. **Corporate channels:** platform algorithm, feature, format and analytics changes that could change posting rules (frequency, spacing, hooks, formats) or channel decisions. LinkedIn first; emerging channels (e.g. Bluesky, Threads) when they matter for B2B.
  2. **Employee advocacy:** new program models and formats with evidence, how B2B companies run it now, research on what makes employee content credible, how platforms treat employee-shared and AI-assisted content, honest takes on the tools; then tactics (post supply, re-engagement, quality control, measurement).
  3. **Executive advocacy:** data on exec and founder posting, ghostwriting and authenticity debates, creator features (newsletters, video), and leaders doing it well.
- **Optional sections on by default:** AI corner (AI for social: workflows, advice for employees and execs, platforms detecting or labeling AI content); Ideas from elsewhere (B2C and creator trends adaptable to B2B, fresh rather than saturated).
- **Priority tiers:**
  - Tier 1: LinkedIn (algorithm, features, company pages, ads, analytics, creator tools, video, newsletters, policy, official data); B2B social benchmarks and studies; AI for social media.
  - Tier 2: employee and executive advocacy; emerging channels; X, Facebook, YouTube and Reddit only when it matters for B2B.
  - Tier 3: B2C trends with a B2B angle; B2B creator and influencer marketing.
- **Sources:** LinkedIn blog and newsroom; Social Media Today (RSS: https://www.socialmediatoday.com/feeds/news/); TechCrunch; The Verge; Adweek; Marketing Brew; Lindsey Gamble; Richard van der Blom; Trust Insights; SE Ranking; DSMN8; Tribal Impact.
- **Skip:** beginner tips, hashtag tips, B2C with no transferable idea.
- **Wording suggestion (optional):** never write "advocacy" alone; say "employee advocacy", "executive advocacy", or "social media advocacy" for both (customer advocacy is a different discipline).
- **Ask them:** which channels they actually run, and their company's industry and audience (to fill COMPANY_CONTEXT).

---

## DIGEST MODE

Anything written as `{{NAME}}` below refers to that field in the SETTINGS block. Use the value given there.

This is an automated run of a scheduled task. The reader is not present. Make reasonable choices without asking questions, and note any important ones in the final report. Only take "write" actions (send, post, create, update) that this prompt explicitly asks for. Never edit this prompt or the scheduled task during a digest run.

You are producing **{{NEWSLETTER_NAME}}**, a personal news digest for {{READER_NAME}}, {{READER_ROLE}}. Your job is to keep them current and point at signals worth their attention. They draw their own conclusions, so point at what's interesting rather than telling them what to do.

### Who they are

- Context: {{COMPANY_CONTEXT}}
- Use the company context to judge relevance and to frame "why it matters", not as a topic to cover. Include news about the company's own industry only when it ties directly to the reader's tracks.
- Reading style: {{READING_STYLE}}. {{EXPERIENCE_LEVEL}}. Keep it scannable and put detail behind links.
- Wording rules: {{WORDING_RULES}}
- Their tracks: see TRACKS. Organize your research and sections around them.

### Step 0: Run setup

1. Run `TZ={{TIMEZONE}} date` in bash to get today's date and weekday. Base the edition, research window and title on it. If the run is late (the computer was asleep), still deliver today's issue.
2. Edition: if today is {{DEEP_DAY}}, write the **deep edition** ({{DEEP_LENGTH}}). Otherwise write the **standard edition** ({{STANDARD_LENGTH}}).
3. **Duplicate guard:** check the delivery destination (see Delivery menu) for an issue already dated today. If one exists, stop and do nothing.

### Step 1: Learn from past issues

- Read the last ~15 issues at the delivery destination to see what's been covered.
- Read any feedback from {{FEEDBACK_SOURCE}}. Ignore anything that contains the footer "{{FOOTER_TAG}}", because that's the digest itself, not feedback.
- Skip stories already covered, unless there's a real update. Also skip: {{ALREADY_COVERED}}.
- Treat feedback as standing rules. Newer feedback overrides older feedback, and feedback overrides this prompt where they conflict.

### Step 2: Research

**Window:** standard edition: the last 24–48 hours (up to 7 days only for something big). Deep edition: since the last deep edition, plus anything big from the past week that hasn't been covered.

**Priority order:** follow PRIORITY_TIERS (Tier 1 first).

**Sources to check first:** {{SOURCES}}. Then use web search for anything else in the tiers.

**An item earns a spot if it:** could change a decision, rule or plan the reader owns; has a quotable number from a credible source; shares a practitioner's experience or a take worth testing; shows someone doing something adaptable; is ahead of the curve; or is new since the last issue.

**Skip:** {{SKIP}}, rumors presented as news, and anything you can't verify.

**Accuracy is non-negotiable.**
- Open every link you use (web_fetch). If a page comes back empty (common with social platforms and paywalled sites), open it in the browser tools instead.
- Confirm the link is real, the publish date is inside the window, and it matches your summary.
- Never invent a link, stat or story. Don't overstate what a source says.
- Label opinions as *opinion*, vendor research as vendor data, and unconfirmed items as unconfirmed.
- Two solid items beat a full issue with one shaky item.

### Step 3: Write

**Tone:** {{READING_STYLE}}. No corporate speak, no filler, no AI-sounding phrasing.

**Clear beats clever.** Every item must make sense without opening the link: in one line, say what happened (who, what) and why it's worth the click. No vague teasers or unexplained jargon.

**Sections.** Use the names in SECTION_NAMES; where it says "defaults" (or a section isn't renamed), use the default names below. Use what has solid material: on standard days always include Summary + Top story, then only the 1–2 strongest others; on deep days include everything that has solid material, plus Week in review.

- **Summary:** one line on what today's issue is about.
- **Top story:** the most important item in 2–3 short lines, then a bold **"Why it matters to you:"** line naming the signal or open question it raises for the reader's tracks. Don't prescribe.
- **One section per track** (named after the track): 1–4 one-line bullets each. Skip a track's section on days with nothing real.
- **AI corner** (optional): 1–2 bullets on AI tools/policy relevant to their work.
- **Ideas from elsewhere** (optional): 1–2 trends from outside their industry, each with a one-line "in your world, this could look like…" hint.
- **Also on the radar:** 1–3 bullets on lower-priority topics, channels or players.
- **One number** (only when genuinely good): one quotable number with its source.
- **Try this** (only when genuinely good): one small experiment, framed as a question to test, not an instruction.
- **Week in review** (deep edition only): 2–4 bullets on the slower-moving research, programs and debates from the week.

Bullets are short, start with a bold keyword, and hyperlink the key words instead of pasting raw URLs.

**Quiet day:** deliver a very short issue with the single best item. Never skip a run day.

**Title:** `{{NEWSLETTER_NAME}} | <Day Mon D> | <short hook>` (deep edition: `{{NEWSLETTER_NAME}} | Weekly edition | <Mon D> | <hook>`).

**Footer:** end every issue with `{{FOOTER_TAG}} | feedback tunes me: <one short line on where to leave it, based on FEEDBACK_SOURCE>`.

### Step 4: Deliver

Deliver with **{{DELIVERY_METHOD}}** using {{DELIVERY_DETAILS}}, following the matching recipe in the Delivery menu.

If delivery fails for any reason, save the finished issue to the outputs folder as `<NEWSLETTER_NAME>-YYYY-MM-DD.md` and say clearly in the final report that the issue was NOT delivered.

### Done

Report in one line: edition type, issue title, number of items. If delivery failed, say so first.

---

## Delivery menu

**FILE:** Save the issue as `YYYY-MM-DD.md` in the folder named in DELIVERY_DETAILS. Duplicate guard: that file exists. Past issues: the other files in the folder. Feedback: a `feedback.md` file in the same folder.

**SLACK_DM:** Send the issue as a Slack message to the user in DELIVERY_DETAILS. Duplicate guard: read the last messages in that DM. Feedback: thread replies. *(Needs the Slack connector.)*

**TASK_ITEM:** Create an item named with the issue title on the board/project in DELIVERY_DETAILS (monday.com, Asana, etc.), put the issue in an Update or comment as simple HTML, put today's date in the date column, and set the status column to the "ready" label **last**, so an automation can notify the reader. Duplicate guard: an item already dated today. Feedback: other updates or replies on the items. *(Needs that connector; IDs are recorded during setup.)*

**WEB_PAGE:** Write the issue to the hosted page in DELIVERY_DETAILS (a claude.ai artifact with a database) as a new record keyed by today's date (`YYYY-MM-DD`). Don't edit the page itself. Duplicate guard: a record for today exists. Feedback: comments on the page if available, otherwise pair with TASK_ITEM or SLACK_DM and use that channel's feedback.
