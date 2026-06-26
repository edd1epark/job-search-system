# Job Search System - Eddie Park

Knowledge base + apply engine for landing a B2B SaaS growth-marketing role.

## What this is

A reusable system that (1) finds best-fit growth roles, (2) builds a tailored resume per role from a master, and (3) drafts signal-based outreach to the founder or hiring manager. The Claude Skill reads this repo as its source of truth.

## Structure

- `master-resume.md` - the superset resume. Every role and bullet. Tailored versions are cut and re-angled from this.
- `positioning-brain.md` - the thinking layer: positioning thesis, growth-stage targeting model, fit-and-foreground logic, the one-line intro, signal-based outreach formula, and the objection map.
- `tone-and-guardrails.md` - the writing rules every output must follow (voice, formatting, what to avoid).
- `sources.md` - where to find roles, the soft ICP filters, fit tiers, and stage tags.

## How the engine uses it

Input: a job link (or a company with no open role).
1. Read `positioning-brain.md` to classify the company's growth stage and score fit (a ranking, not a gate).
2. Select and foreground the right experience blocks from `master-resume.md`.
3. Apply `tone-and-guardrails.md` to every line.
4. Output: a tailored 1-page resume, a one-line personalized intro, and a signal-based outreach message.

## Status

Living document. Update the master and the brain as the story sharpens; the engine always reads the latest.
