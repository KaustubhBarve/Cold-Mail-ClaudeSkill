# cold-mail

A [Claude Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) that researches and drafts cold emails and cold outreach messages that actually get replies — sales outreach, investor pitches, recruiting messages, partnership asks, and follow-ups.

It doesn't just fill in a template. It researches the recipient, picks a persuasion structure that fits the actual situation, and drafts something that reads like it was written by a person who checked first.

## Why this exists

Most "write me a cold email" output is generic because it skips the one step that actually moves reply rates: real, specific research about the recipient. This skill treats that as the highest-leverage part of the job, not an afterthought — and it's built around principles that don't expire with the next growth-hacking trend, rather than tactics tied to a specific platform or algorithm quirk.

Concretely, the skill:

- **Researches before writing.** Uses web search to build a short dossier on the individual, their company, and their industry — then picks *one* accurate, relevant hook instead of stacking everything it found.
- **Picks a structure, not a vibe.** Chooses from a library of 12 named persuasion frameworks (Trigger-Event, Problem-Agitate-Solve, AIDA, Before-After-Bridge, and others) based on the actual situation, and explains why that framework fits.
- **Refuses to fabricate.** Won't invent a stat, a case study, a comparable customer, or a recipient's name it doesn't have. If a data point isn't real, it's left out — not guessed.
- **Adapts to channel.** Produces email, LinkedIn DM, SMS, or cold-call-script shaped output depending on what's actually being sent, instead of defaulting to email formatting everywhere.
- **Plans the follow-up, not just the first email.** Most replies come from touch 2–4, not the first message — the skill drafts a realistic follow-up cadence and knows when to stop.

## What's in this repo

```
cold-mail/
├── SKILL.md          # Entry point: the 6-step workflow Claude follows
├── frameworks.md      # Library of 12 persuasion frameworks with skeletons
└── README.md          # You are here
```

`SKILL.md` is what Claude reads first. It stays lean and delegates to `frameworks.md` only when it's time to pick and fill in a specific structure — this keeps the skill fast to load and easy to extend.

## The workflow

1. **Get the essentials** — offer, recipient, goal, constraints (tone, length, channel). Works fine with partial info; asks one targeted question only when something essential is truly missing.
2. **Research** — real web search on the individual, company, and industry. One accurate hook beats five stacked ones.
3. **Pick a framework** — one of 12 structural skeletons, chosen to fit the situation, never combined.
4. **Draft** — subject line about them, one value proposition, one CTA, no fabricated stats, sounds like a person.
5. **Plan the follow-up** — a realistic 4-touch cadence that stops the moment someone replies.
6. **Present** — shaped to the actual sending channel, with the research hook shown explicitly so the sender can sanity-check it before anything goes out.

Diagnostic requests ("improve my reply rate," "what's wrong with my outreach") skip straight to a prioritized checklist instead of forcing a fabricated draft.

## The framework library

| Framework | Best for |
|---|---|
| Trigger-Event | Something newsworthy just happened to them |
| Problem-Agitate-Solve | They already feel a known pain point |
| AIDA | Strong ICP fit, need to show the mechanism too |
| Before-After-Bridge | Value is easiest to grasp as a contrast |
| Praise-Picture-Push | A genuine, specific, verifiable achievement to acknowledge |
| Quick-Question | Time-strapped exec, want the highest reply rate for the least reading |
| Right-Person Redirect | Not sure this is even the right contact |
| Introduction Request | No warm path in, but a plausible connector exists |
| Competitor-Mention | They currently use a known competitor |
| Data-Backed / Social-Proof-Led | Long sales cycle, need credibility fast |
| Value-Give / No-Ask | Want to open a relationship with no immediate ask |
| Warm-Signal Follow-Up | They already interacted with the sender's content or site |

Each entry in `frameworks.md` includes *why it works* — the underlying human tendency it draws on — not just the copy-paste shape, so Claude adapts it instead of templating it.

## What it won't do

- Guess a name it doesn't have.
- Invent a customer, a result, or a statistic to sound more credible.
- Stack two frameworks into one email, or send the same message reworded as "variants."
- Advise on deliverability infrastructure (SPF/DKIM/DMARC, sending reputation, list quality) — that's a separate, fast-moving problem outside this skill's scope.

## Installing

This is a [Claude Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) — a folder Claude reads to extend what it knows how to do well.

- **Claude.ai / Claude apps:** upload the packaged `.skill` file (or this folder) wherever your client supports installing skills.
- **Claude Code / Cowork:** drop this folder into your skills directory (e.g. `~/.claude/skills/cold-mail` or your project's configured skills path).

Once installed, just ask normally — "help me reach out to this VP before Monday," "write a follow-up for this investor who went quiet," "improve my cold email reply rate" — and Claude will pull in the skill automatically.

## Usage examples

```
"Draft a cold email to the VP of Engineering at a Series B fintech —
I don't have her name yet. I sell code-review automation."

"Write a follow-up for an investor who's gone quiet — pitched them
10 days ago, no news since."

"Research this company before I email their founder, then draft
the outreach."
```

## Contributing

Issues and PRs welcome. If you're proposing a change to `SKILL.md` or `frameworks.md`, it helps to include the specific prompt that exposed the gap — this skill was built and refined against adversarial test cases (unknown names, empty research, conflicting channel formats, missing proof points), and new changes are easiest to evaluate the same way.

## License

MIT (or update to whatever license you're publishing under).
