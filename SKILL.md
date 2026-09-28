---
name: product-design-job-search-workflow
description: Screening-first job search system for UX and product designers at any level in the US and Canada. First use runs a short intake and saves a reusable profile. Then use it whenever the user pastes a job link or JD, asks if a role is worth applying to, wants a tailored resume, cover letter, or application answers, wants their tracker updated, or asks why they are not getting callbacks. Trigger on a bare job URL and on phrases like "screen this", "should I apply", "worth it?", "tailor my resume for", "set up my job search".
---

# Job Search Workflow

Screen hard, apply narrow, tailor honestly, track everything. Most wasted effort goes to roles that were never going to work, so the screen runs before any writing.

## Output rules (always)

Token budget matters. Every reply follows these:

- Lead with the answer. No preamble, no recap of what the user said, no restating the JD.
- Screens use the format below and nothing else unless asked.
- Resume drafts show only what changed from the master, not the full resume, unless asked.
- Load a reference file only when the step needs it. Do not re-read files already read this session.
- Fetch a posting once. If walled, ask for the paste (see `references/fetch-notes.md`).
- Edit files in place (string replacement). Never regenerate a whole file to change one row.
- No options menus when one answer is clearly right. Offer options only for copy choices.
- Do not re-raise an open item the user ignored. Do not suggest roles they did not paste.

## Step 1: Profile

Look for `job-search-profile.md` in the project or working directory.

- **Found:** treat it as authoritative. Go straight to the request.
- **Missing:** run intake first (`references/intake.md`), even if the user opened with a job link. One line: "I need about 10 minutes to set your criteria first, or I'd be guessing your comp floor and dealbreakers." If they refuse, run a one-off screen and mark which steps were guessed.

Intake writes `job-search-profile.md` per `references/profile-schema.md`. After saving, give a 5-line orientation: what to paste, that resume text comes before any PDF, when cover letters happen, how to report responses, how to change criteria.

## The screen

Cheapest checks first. Stop at the first failure and name it. Never soften a fail into a maybe.

1. **Hard exclusions.** Any hit from the profile is a skip.
2. **Geography and onsite.** Check the profile's yes / conditional / no lists and the days-in-office ceiling. Relocation is a stop unless the profile allows it.
3. **Comp.** Test the band midpoint against the base floor, not the ceiling. Equity is additive, never a substitute for base. At large companies with wide bands, ask for target level and equity before ruling out on base. No band posted in a jurisdiction that requires one (e.g. CA, CO, NY, WA, BC, ON): flag it and ask the recruiter before investing time.
4. **Level and title.** Titles scale with company size. Read what the role owns, then compare to the profile's title targets by company size. Do not skip a lower or untitled posting at a large company when comp clears.
5. **Ownership.** Level-relative (profile records the reading). Junior/mid: a design team and someone senior to learn from. Senior: owns a product area, design is strategic. Staff+: cross-team scope and a real IC ladder above.
6. **Domain fit.** Against the profile's target domains.
7. **Durability.** If the currently hyped technology stopped advancing today, would the customer problem still exist at the same size? No is a skip. Early-stage companies also need named investors or named customers. Recent acquisitions or layoffs lower the tier; they do not auto-skip.

Soft flags are weighed, never auto-skip: years asked slightly above the user's, domain evidence only in older work, title a notch off.

**Multiple roles at one company:** recommend one, the strongest fit, not the highest title. Flag only if the teams are unrelated.

### Screen output format

```
**Company · Role** · Apply (Tier) | Skip (step N: reason)
Comp: band, midpoint vs floor
Flags: soft flags, or "none"
Next: one line (draft resume / ask recruiter X / paste JD)
```

Four lines. Add a fifth only for something that changes the decision.

## Tiers

- **Dream:** few, worth a stretch.
- **Sweet spot:** right size, real domain fit. Most applications.
- **Safety net:** large stable employers, fine fit, slower.
- **Practice:** interview reps only. Useful early. Once the user reaches onsites, recommend dropping it and record the date so it is not relitigated.

## Application workflow

1. Fetch the posting.
2. Screen.
3. On Apply: draft tailored resume text in chat (`references/resume-system.md`). "Draft" means text only. No PDF until the user asks.
4. Build the PDF on approval with `scripts/resume_builder.py`, then verify.
5. Cover letter or application answers only with a real hook (below).
6. Update the tracker when the user reports an application or response.

## Cover letters

Write one only with a genuine personal stake or a specific domain hook. A thematic bridge is not a hook; a constructed connection reads as performed and is worse than no letter. Skip when the application has multiple written questions, since those are the letter. Never quote the company's marketing copy back to them. Match their category nouns, never their phrasing.

## Outreach

Warm outreach converts far better than portal volume and runs alongside it by default. Sequence: apply, then message an IC designer on the team with a specific peer question, then the design lead a few days later. Never both on the same day. Some companies cap referrals per period; the profile tracks referral sources and limits, so spend them on the strongest fits.

## Reading rejections

Where rejections cluster is the signal.

- Low tiers rejecting while top tiers stay open: level is not the filter.
- Rejections everywhere, including roles below target: materials or positioning.
- Recruiter-screen rejections with no team contact: often comp, level, or location mismatch. Ask for feedback and for other open teams.
- Cold portal conversion in the low single digits is normal and not evidence on its own.

Before recommending the user aim lower, state the cost in numbers: pay, title, time to climb back. If the evidence does not support it, say so.

## Tracker

One markdown file, dated filename (`job-tracker-YYYY-MM-DD.md`), format in `references/tracker.md`. Three piles: In progress (top), Active, Closed. Each pile sorted by last update, newest first.

## References

- `references/intake.md`: first-run interview and level calibration
- `references/profile-schema.md`: profile structure
- `references/resume-system.md`: tailoring rules, build, verification
- `references/tracker.md`: tracker format and edit rules
- `references/fetch-notes.md`: job board fetch behavior
- `scripts/resume_builder.py`: PDF generator with auto-fit and validation

## Integrity

Be decisive. "It depends" is not a screen.

Never invent metrics, keywords, or claims the user cannot defend in an interview, including for ATS coverage. A padded keyword exposed in an interview costs more than the screen it passed. When the user corrects a fact, take the correction exactly as stated and add it to the profile's banned or locked lists if it should stick.
