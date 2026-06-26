---
name: apply-to-role
description: >
  Turn a startup growth/marketing job into a tailored, send-ready application for Eddie Park:
  a resume re-angled for the role, a personalized intro line, an outreach message to the
  founder or hiring manager, and-when the situation warrants-a bespoke outreach strategy.
  Use when given a job link, a company + role, or asked to "apply to," "draft outreach for,"
  or "tailor my resume for" a role, or to batch-draft across the Strong-tier rows in the
  Airtable tracker. Reads the canonical career knowledge base from GitHub so every output
  stays on-story.
---

# Apply-to-role engine (Eddie Park)

Research before writing: read the full job post and follow its links, look at the product, the
founder, and recent press, and draft from what that surfaces. A human-approval gate sits before
anything is sent.

**Inputs (any of):**
- A job link (Ashby / Greenhouse / Lever / Rippling / workatastartup / Consider board).
- A company + role (no link).
- A great-fit company with **no open role** (proactive founder outreach).
- "Batch the Strong tier" -> iterate the Airtable view, draft for each.

**Outputs per role:**
1. A **tailored resume**, re-angled for the role. Length follows the role - do not force one page.
2. A **personalized intro line** for the top of the resume and first line of outreach.
3. An **outreach message** to the decision-maker, written from a real signal (guidelines below).
4. **[Conditional] A bespoke outreach strategy.** If the signals - including anything in the job
   post - present a standout opening or warrant a more personalized approach than a single
   message, you are **required** to propose it (see Step 4d).

All outputs are written back to the Airtable row. Nothing is sent; Eddie reviews and sends.

---

## Step 0 - Load the knowledge base (always, first)

Read these raw files before anything else; they are the single source of truth:
- https://raw.githubusercontent.com/edd1epark/job-search-system/main/master-resume.md
- https://raw.githubusercontent.com/edd1epark/job-search-system/main/positioning-brain.md
- https://raw.githubusercontent.com/edd1epark/job-search-system/main/tone-and-guardrails.md
- https://raw.githubusercontent.com/edd1epark/job-search-system/main/sources.md

Never invent experience. Everything must trace to the master resume.

---

## Step 1 - Read the role & classify

1. Fetch the job post in full. Extract company, exact title, location, must-haves, the
   "you will own" lines, stage hints (team size, funding, ICP), and the ATS apply URL.
2. **Follow what the post points to.** If it links to or references a video, article, person,
   or deck (e.g., "think of this role as our [Name]"), go research it: watch/read it and
   understand what they actually want. If you cannot access a video, ask Eddie to fetch the
   transcript before finalizing - do not skip it. These references are often the strongest
   personalization material in the whole application.
3. **Classify growth stage** (Seed -> Series A/B -> C+/pre-IPO/public) using positioning-brain.md section 2.
   Stage decides what to foreground and whether a service offer is appropriate.
4. **Score fit** (Strong / Good / Stretch) with a one-line reason, per sources.md. Be honest.

## Step 2 - Find the decision-maker

Goal: founder or hiring manager - name, title, LinkedIn, email. Work down this stack, stop
when you have enough:
1. **Board-native founder details** - workatastartup company profiles; Consider boards'
   "Show founder details" toggle. Often already present.
2. **Company /about, /team, /company page** - names and titles from the source.
3. **Apollo** - primary contact + email. Title-target: Founder/CEO, Head of Growth, Head of Marketing, CMO.
4. **Apify** - a LinkedIn company-employees actor to locate by title; an email finder/verifier actor for the address.
5. **Web search fallback** - "Head of Growth at {company}", "{company} founder".

If email is still missing, infer the pattern (first@domain / first.last@domain) and verify it;
flag any unverified address rather than treating it as confirmed.

## Step 3 - Gather signals (positive openings, never criticism)

You are looking for **genuine things to admire or connect over** that open a conversation -
not weaknesses to point out. Never lead from criticism. Rank by reliability; never block on
the hard ones.

- **Role signal (free, always):** what the job post tells you they care about, plus anything it links to (Step 1.2).
- **Product signal (free, web fetch):** a feature they recently shipped, a smart product decision, the problem they're solving and why it's interesting. Frame as admiration.
- **Company / press signal:** recent funding, a launch, a milestone, a notable customer. Recent press and raises are great openers ("congrats on the {round}").
- **Founder / person signal:** a recent LinkedIn or Twitter/X post or public take of theirs. Eddie has LinkedIn and Twitter/X post-scraper actors set up in Apify - use them to pull the founder's recent posts. Also look for shared background or common ground.

Record the single sharpest, most genuine signal; it anchors the message.

## Step 4 - Generate

### 4a. Tailored resume
- Start from master-resume.md. Apply the **foreground table** in positioning-brain.md section 3 for the role's lean (founding / CRO / PMM / content / performance / AI-growth): lead with the matching blocks, trim the peripheral, keep the pivot narrative spine intact.
- **For early-stage / seed roles, foreground the early-startup experience (Vandalsoft):** joining a startup early, helping raise seed, and launching real products is proof Eddie thrives in 0-to-1 chaos. It's an asset here, not something to trim.
- **Always lead the Gro.X section with the $103K revenue / 15 B2B SaaS clients bullet** - it gives instant context. Tailor the order of the bullets that follow it per the role.
- Re-angle the title/intro line per the stage. Apply every rule in tone-and-guardrails.md (bold accomplishments not tools; no em-dashes; no summary/skills block). **Length follows the role; do not force a single page.**
- Render with the existing generators: generate_ats_resume.js (ATS .docx) and build_designed_resume.py (designed PDF). Output Eddie_Park_Resume_{Company}.docx / .pdf.

### 4b. Personalized intro line
One line, about them first, re-angled from the default in positioning-brain.md section 4.

### 4c. Outreach message - guidelines first, template second

This is judgment, not a form. Write the message that a real, sharp candidate would send after genuinely looking into the company. Hold every draft to these guidelines:

- **Open with a real signal that builds rapport** - specific and genuine, never generic.
- **A sharp market/category insight is one of the strongest openers** - e.g., naming a real gap the company is positioned to win ("a gap in local-SMB data vs Apollo/ZoomInfo"). It proves he speaks B2B SaaS fluently. Use only when genuinely true.
- **Reflect the job post back** - a line like "I read the post and it felt like a strong fit: you want someone who builds in public, runs fast experiments, and is AI-native" shows he actually read it and mirrors their language.
- **Make it clear he's a candidate interested in the role**, not a vendor. Naming the role early does this (his LinkedIn still says "Founder, Gro.X," so the default read is sales - defuse it).
- **Low pressure.** No sales CTA. Never "worth a quick chat?" or anything that sounds like booking a demo.
- **Scannable for a busy founder** - short, a few lines, not a wall of text.
- **Direct, respectful, and human** - sound like a person, not a sequence.
- **If you have a sharp, correct insight** (not criticism) that shows he speaks B2B SaaS, you can include it - only when it's genuine.
- **Offer the conversion audit only when the role and company stage make it natural** (early/mid stage where conversion is a live problem). Otherwise leave it out.

Opening-line formats (always anchored to a real signal):
- "Loved your take on {industry change}."
- "Loved that new feature you introduced to {product}, because {reason}."
- "Loved {thing} about your background - we have that in common."
- "Loved what {Company} is building, because {reason}."

Sample template (a starting point, not a cage):

> Hey {first_name},
> Love what you're building with {specific, genuine insight}.
> I saw you're hiring a {role} and wanted to introduce myself.
> {one situational line - a sharp insight, common ground, or the conversion-audit offer}
> Would love to hear where you're taking {Company}. Looking forward to your thoughts.

Situational lines (pick what fits, or write a better one):
- **Conversion-audit offer (when stage fits):** "I previously ran a B2B SaaS CRO agency, and I'd love to offer a quick conversion audit on turning more of your traffic into demos."
- **Connect / direction:** "Would love to connect and hear where you're looking to take {Company}."
- **Insight / common ground:** a genuine "loved your take on {industry shift}" or "loved {thing} about your background - we have that in common."

For a **no-open-role** prospect, drop the role line; lead with the signal and a light "wanted to be on your radar as you scale."

### 4d. [Conditional] Bespoke outreach strategy - required when warranted

If the research surfaces a standout opening - a job post that references a person/video/idea, a founder who clearly values a specific style, a recent moment worth a more creative move - you are **required** to propose a tailored strategy beyond the standard message. Example: a Lassie growth role that says "think of this role as Lassie's Matt Epstein" and links a video - review the video (or ask Eddie for the transcript), understand that growth archetype, and build outreach that speaks to it directly (and angle the resume to match). Spell out the angle, why it fits the signal, and the concrete move (e.g., a short Loom teardown, a mini-campaign idea, a reference to the cited person's playbook). Only raise this when there's a real opening - don't manufacture one.

## Step 5 - Write back & hand off (no sending)

- Update the Airtable row: Status -> "Drafted"; store the outreach message, the chosen signal, the decision-maker, and any strategy note in the existing fields.
- Save the resume files to the outputs folder and present them.
- Surface the contact, the message, and (if any) the strategy for Eddie to review. **Eddie sends - the skill never sends, never submits a form, never emails on his behalf.**

---

## Guardrails
- If you can't find a genuine signal, say so - don't fabricate one.
- Source-of-truth is the GitHub KB; re-read it each run.
- Honesty: tell the pivot story straight; never lead with the runway detail; tier fit truthfully.
- Tone: clear over clever, 6th-8th grade, accomplishment-first, no em-dashes, no buzzword stacks.
- Never criticize the prospect's product as an opener.
- Privacy/safety: don't send messages, submit applications, or email without explicit human action; flag any unverified email.
- The "could a competitor paste this onto their resume?" test applies to every line.
