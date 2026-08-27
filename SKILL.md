---
name: product-design-job-search-workflow
description: A screening-first job search system for product designers at any level. On first use it interviews the user about their level, comp floor, geography, and dealbreakers, then writes those into a reusable profile. After that, use it whenever the user pastes a job link or JD, asks whether a role is worth applying to, asks for a tailored resume or cover letter, wants to update their application tracker, or wonders why they are not getting callbacks. Trigger on a bare job URL with no other context, and on phrases like "should I apply to this", "screen this", "worth it?", "tailor my resume for", "set up my job search".
---

# Job Search Workflow

A screening-first system for product designers running a real search. Most wasted effort in a job search goes to roles that were never going to work. Screen hard, apply narrow, tailor properly, track everything.

The screen only works with the user's actual numbers. A generic screen approves roles that fail their real dealbreakers, which is the expensive failure mode. So the first thing this skill does is get those numbers.

## Step 1: Check for a profile

Look for a file named `job-search-profile.md` in the project or working directory.

**If it exists:** read it, treat it as authoritative, and go straight to whatever the user asked for. Do not re-run intake.

**If it does not exist:** run intake before anything else, even if the user opened with a job link. Say so briefly: something like "Before I screen this, I need about ten minutes to set up your criteria, otherwise I'd be guessing at your comp floor and dealbreakers." Then follow `references/intake.md`.

If the user declines intake and wants a one-off screen, do it, but flag which steps were guessed.

## Step 2: Intake

Read `references/intake.md` and run it. It covers how to draft from a resume first, what to ask in what order, how to push back on vague answers, and how thresholds shift by level.

Output is `job-search-profile.md`, built to the structure in `references/profile-schema.md`. Save it and tell the user to keep it in their project so it loads in every future conversation.

## Step 3: Explain the workflow

After the profile is written, give the user a short orientation. Not a manual. Roughly:

- What to paste to get a screen, and what you will hand back
- That resume text comes before any PDF gets built, so they approve wording first
- That cover letters get written only when there is a real hook
- That the tracker is a file you maintain, and they should report responses as they come
- One line on how to change criteria later

Keep it under a dozen lines. They can learn the rest by using it.

## The screen

Run in order, stop at the first failure, name the step that failed. Do not soften a failure into a maybe.

1. **Level and scope.** Titles scale with company size. The same scope carries different titles at a 200-person company and a 200,000-person one. Read what the role actually owns, then check it against the level targets in the profile.
2. **Ownership.** Level-relative, and the profile records what it means for this user. For a junior or mid designer, the question is whether the role puts them somewhere they can grow: is there a design team, is there someone senior to learn from, is the scope real work rather than ticket cleanup. For a senior, it is whether they own a product area and design is treated as strategic. For staff and above, it is whether the scope crosses teams and whether the IC ladder above them actually exists.
3. **Geography.** Check against the profile's yes, conditional, and no lists. Relocation is usually a hard stop unless the profile says otherwise.
4. **Onsite requirement.** Compare posted days in office against the profile ceiling.
5. **Compensation.** Usually the gate that should stop promising roles. Test the midpoint of the posted band, not the ceiling. A midpoint below the floor means the offer has to max the range to work. Wide bands at large companies are normal and equity can be a real share of the package, so ask for target level and equity before ruling out on base alone.
6. **Hard exclusions.** Any hit is a skip. No weighing.
7. **Durability.** If the technology currently hyped in the field stopped advancing today, would this company's customer problem still exist at the same size? No is a skip. This catches companies whose product is a wrapper on a trend.

Note soft flags separately. Soft flags are weighed, never auto-skip: years asked slightly above what the user has, domain evidence that exists in their history but not recent work, a title a notch off target.

**Multi-role at one company:** recommend one application unless the teams are genuinely unrelated. Pick the strongest fit, not the highest title.

## Tiers

Sort targets into tiers.

- **Dream:** the small set worth a stretch application.
- **Sweet spot:** correctly sized, domain fit is real. Most applications live here.
- **Safety net:** large stable employers, fine fit, slow process.
- **Practice:** roles the user does not actually want, applied to for interview reps.

Practice tier is useful early and for designers who have not interviewed recently. Once the search has volume and the user is getting to onsites, it becomes a tax on attention and produces rejections that distort the read on the search. Recommend dropping it at that point and record the decision with a date so it does not get relitigated.

## Reading rejections

Where rejections cluster is the signal.

- Clustering in the lowest tiers while top tiers stay open means level is not the filter.
- Clustering everywhere, including roles clearly below target, points at materials or positioning.
- Cold portal conversion in the low single digits is normal. A low number is not evidence of a mispriced target on its own.

Before recommending the user aim lower, count the cost out loud: pay, title, and the time to climb back. Give the number. If the evidence does not support it, say that instead.

## Application workflow

When the user pastes a link or JD:

1. Fetch it. See `references/fetch-notes.md` for board quirks and when to ask for pasted text.
2. Run the screen. Yes or skip, with the failing step named.
3. On a yes, draft tailored resume text for review before building anything. See `references/resume-system.md`.
4. Build the PDF only after the user approves the text, then verify it before delivering.
5. Draft a cover letter or application answers only when the hook is real.
6. Update the tracker.

## Cover letter policy

Write one when there is a real personal stake or a specific domain hook. Skip otherwise, because a letter without one becomes a skills recital the resume already covers.

**A thematic bridge is not a hook.** If the connection has to be constructed, it reads as performed and the letter is worse than none.

Skip when the application already has multiple written questions. Those are the cover letter.

Never quote the posting's marketing copy back at them. Match their category nouns, never their phrasing.

## Tracker

Maintain one markdown file, pipe-delimited table, columns: Company, Role, Tier, Applied, Status. Date the filename. Update it in the same session the user reports a response, using string-replacement edits rather than regenerating the file so nothing silently drops.

## Reference files

- `references/intake.md`: the first-run interview. Read before Step 2.
- `references/profile-schema.md`: structure of the profile file to write.
- `references/resume-system.md`: tailoring rules and PDF build pipeline.
- `references/fetch-notes.md`: job board fetch behavior.

## Working style

Be decisive. A screen that ends in "it depends" is not a screen. Name the failing step and move on.

Never invent metrics, keywords, or claims the user cannot defend in an interview, including for keyword coverage. An interview that exposes a padded keyword costs more than the screen it passed.
