---
name: cold-mail
description: 'Research and draft cold emails and cold outreach messages that actually get replies. Trigger this whenever the user wants to write a cold email, sales outreach email, prospecting/BD email, investor outreach, recruiting or candidate outreach, partnership pitch, or any first-touch message to someone who doesn''t know them yet — including requests like "help me reach out to a lead," "write a follow-up/breakup email," "improve my cold email reply rate," "personalize this outreach," or "research this company/person before I email them." Handles the full workflow end-to-end: pinning down the sender''s offer and goal, researching the recipient/organization/industry via web search, choosing the right persuasion framework for the situation, and producing a ready-to-send draft (subject line, body, and follow-up sequence).'
---

# Cold Mail

A cold email gets noticed for exactly two reasons: it's clearly *about the reader*, and it says that in a shape the reader's brain already recognizes as worth finishing. This skill exists to do both, reliably, without depending on whatever tool or trend happens to be popular right now.

## Design principle: build on what doesn't expire

Email platforms, subject-line hacks, and "growth hacks" churn constantly. What doesn't churn is *why* a message earns a reply: relevance to the reader, a recognizable structure that respects their time, and one easy next step. AIDA is over a century old and still works because it's a description of human attention, not a platform feature. That's the bar for everything in this skill — if a tactic only works because of a current algorithm quirk or a specific tool's feature, it doesn't belong here. If it works because of how people have always decided what's worth reading, it does.

Practical consequence: don't lean on any specific sending platform, and don't treat any hardcoded statistic (open rates, reply rates, "best" send times) as gospel — those move year to year and by industry. If the user asks for current benchmarks or trends, use web_search to get a fresh number rather than relying on training data, and say so if numbers are illustrative rather than current.

## Workflow

### First, check what's actually being asked

Most requests want one specific, sendable draft — that's what Steps 1–6 below produce. But some requests are diagnostic instead: "improve my reply rate," "what's wrong with my outreach," "give me general cold-email advice" — with no specific recipient, offer, or draft in view. Forcing the numbered workflow onto a data-free request means either stalling to interrogate before saying anything useful, or inventing a fake sender/recipient just to have something to draft — both are worse than the alternative.

For a diagnostic request: skip straight to a compact, prioritized checklist pulled from Steps 2, 4, and 5 below (roughly in order of impact — personalization depth, subject line, opening line, one CTA, follow-up cadence), grounded in this skill's own principles rather than generic outside tips. Then ask, at most, one lightweight follow-up ("Want me to go through a specific draft or target?"). The checklist should be immediately useful on its own, whether or not they answer it.

If a specific recipient, offer, and goal *are* given (even partially), proceed through the numbered steps below as usual.

### Step 1: Get the essentials

Before researching or writing anything, make sure you know:

- **The offer, in one plain sentence.** What the sender does, for whom, stated the way a human would say it out loud — not the pitch-deck version.
- **The recipient.** Name, role, company — whatever the user has. It's fine to work with partial information (e.g., "VP of Engineering at a Series B fintech, don't know their name yet").
- **The goal of this specific email.** A reply, a booked call, a click, an introduction to the right person — these need different CTAs.
- **Constraints.** Tone (formal vs. casual), length limits, channel (email vs. LinkedIn DM vs. a script for a cold call), anything the sender explicitly wants avoided.

If something essential is missing and can't be reasonably inferred from context, ask one targeted question rather than guessing wrong — but don't interrogate the user for a five-field form when a reasonable default exists.

### Step 2: Research (this is the part that makes it get noticed)

This is the highest-leverage step. A well-structured email with no real personalization reads as a template; a mediocre structure with one genuinely specific, relevant detail reads as a person paying attention. Use `web_search` (and `web_fetch` for a specific page the user or search results point to) to build a short dossier before writing anything:

- **The individual** (if named): current role and how long they've held it, anything they've publicly said or written recently (talks, posts, interviews), notable recent moves.
- **The organization**: recent funding, product launches, hiring signals, leadership changes, press coverage, how they position themselves against competitors.
- **The industry**: what's currently a live pain point or shift for this role/sector — this matters even when you can't find anything on the individual or company specifically.

Two things to hold onto from this step:

1. **Pick one hook, not five.** Citing a single, accurate, relevant detail reads as attentive. Stacking several reads as surveillance. If research turns up three good angles, choose the one most tied to the offer and let the rest go.
2. **Paraphrase, never lift.** When pulling from an article or press release, restate it in your own words — don't quote it, and don't invent a detail you didn't actually find. An inaccurate personalization line is worse than a generic email; it tells the reader you didn't actually check.

If research comes up empty (obscure company, no public individual info), that's fine — fall back to an industry-level hook or one of the frameworks built for exactly that situation (see Step 3).

### Step 3: Pick a framework

Frameworks are structural skeletons, not scripts — they encode *why* a message holds attention, and the wording should be rewritten every time to sound like the sender, not like a template. Full library with skeletons and the psychology behind each one is in `frameworks.md`. Quick map from situation to framework:

| Situation | Framework |
|---|---|
| Something newsworthy just happened to them (funding, launch, award, new role) | Trigger-Event |
| They likely already feel a known pain point in this role/industry | Problem-Agitate-Solve, or AIDA if you also want to show *how* you solve it |
| You want them picturing life after your product | Before-After-Bridge |
| You have a genuine, specific compliment tied to something they did | Praise-Picture-Push |
| Time-strapped exec, want the highest reply rate for the least reading | Quick-Question / three-sentence format |
| You're not sure this is even the right contact | Right-Person redirect ask |
| You know of no warm path in at all | Introduction request |
| They currently use a known competitor | Competitor-mention |
| Long sales cycle, need credibility fast (enterprise, high price point) | Data-backed / social-proof-led |
| You want to lead with something useful and no ask | Value-give |
| They already interacted with the sender's content or site | Warm-signal follow-up |

Never combine two frameworks in one email — pick the one that fits the situation and commit to its shape.

### Step 4: Draft

Whatever framework you chose, hold to these — they're the parts of a cold email that don't go out of style:

1. **Subject line is about them, not you.** It's the reader deciding whether the next line is worth their time. Short, specific, no clickbait, no spam-triggering words (free, act now, guaranteed, $$$) — filters and human skepticism have penalized these for decades and will keep doing so.
2. **Opening line earns the second line.** Never open with "My name is X and I work at Y" — that's information the reader doesn't yet care about. Open with something about them.
3. **When the recipient's name isn't known, don't guess one.** A wrong guessed name reads worse than no name at all. Use a role-neutral opener instead ("Hi there," or a first line with no salutation at all, whichever fits the channel) rather than leaving a literal `{{name}}` placeholder or inventing one. Note it to the sender in Step 6: a named greeting will likely outperform this once they have the name, so it's worth a quick check before sending if there's time.
4. **One idea, one value proposition.** Resist the urge to list everything the product does. Say the one thing that matters for this reader.
5. **Quantify the benefit when you honestly can.** "Saves engineering teams review time" is weaker than a concrete number — but never fabricate a stat to sound more precise. This applies just as much to comparable-company case studies (a named or implied company that used the product and got a specific result) as to raw numbers: don't invent one to fill a framework's proof-point placeholder. See `frameworks.md` for how to handle a proof-point placeholder you don't have real data for.
6. **Exactly one CTA.** One ask, easy to say yes to. Don't offer three ways to respond — more options lower response rates, not raise them.
7. **Short enough to read in the time it takes to open it.** There's no magic word count — the discipline is saying one thing well, not hitting a number. If you're padding to sound substantial or cutting a sentence that's doing real work just to be brief, both are wrong.
8. **Sounds like a person.** Plain language, contractions are fine, no corporate superlatives ("revolutionary," "game-changing", "synergy"). Match the tone the sender actually asked for.

Before presenting a draft, run this self-check:
- Count "you/your" vs. "I/we/our" — the email should be about them more than about the sender.
- Would the recipient find the personalization accurate and normal, not unsettling, if they thought about how you knew it?
- Is there really only one ask?
- Would this have worked ten years ago, and will it still work ten years from now? If the only reason it works is a current platform quirk, rework it.

### Step 5: Plan the follow-up

Most replies come from follow-ups, not the first email — this has held true regardless of channel or era because inboxes have only ever gotten more crowded, never less. A simple, evergreen cadence:

1. **Day 1** — the initial email.
2. **~2–3 days later** — a short follow-up, different angle or added value, not just "bumping this up."
3. **~5–7 days later** — another angle, maybe the piece of social proof or resource not used yet.
4. **~10–14 days later** — a final, low-pressure "close the loop" email that makes it easy to say no and easy to say "not now, try me later."

Stop the sequence immediately if the person replies at all, including to decline. Never send a fifth follow-up on someone who's gone quiet after four — that reads as pressure, not persistence.

If a specific touch genuinely has no new angle or update to add, don't invent one just to fill the slot — a fabricated update reads worse than an honest one. Shift that touch to the low-pressure "close the loop" tone early instead: acknowledge there's nothing new, make declining genuinely easy ("no worries either way," "let me know if it's not a fit"), and leave the door open rather than manufacturing urgency or progress that isn't real.

### Step 6: Present the draft

Show the research hook explicitly (e.g., "Personalization used: they raised a Series B in March") so the sender can sanity-check accuracy before sending — never send something the sender hasn't seen.

**Match the output shape to the channel captured in Step 1 — don't default to email formatting for every channel:**

- **Email** (the default if no channel was specified): subject line, then body, then sign-off.
- **LinkedIn DM or other social/direct message:** no subject line, shorter and more casual than an email norm, no formal sign-off block. If `message_compose_v1` is available, use `kind: "other"`, not `kind: "email"`.
- **Text/SMS:** shorter still, no subject line, casual register. Use `kind: "textMessage"` if available.
- **Cold-call script:** structurally different from a written message, not just a shorter one — write it as a spoken opener (who you are / why it's relevant / one question), plus a couple of likely-objection responses, rather than an email read aloud.

If a message-composing tool is available in the current environment (for example `message_compose_v1` in claude.ai), use it with the `kind` matching the channel above to present 2–3 labeled variants representing genuinely different strategic angles (e.g., "Trigger-event" vs. "Data-backed" vs. "Quick-question") rather than the same message with different adjectives — this lets the user pick the approach, not just the wording. Include the subject line for each variant when the channel is email.

If no such tool is available, present the draft(s) as plain text in the shape appropriate to the channel — for email, that means subject line then body, no markdown headers or bullet formatting inside the email itself (an AIDA-style capability list is the one common exception).

## A note on what this skill doesn't cover

Whether an email reaches the inbox at all depends on separate technical factors — sending domain reputation, authentication (SPF/DKIM/DMARC), list quality, sending volume and pacing. These matter, but they're infrastructure decisions that change faster than copywriting fundamentals and depend on whatever the sender is using to actually send mail. This skill focuses on what the email says; point the user to their sending platform's current documentation for the infrastructure side rather than relying on specifics baked in here.
