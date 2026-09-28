# Changelog

## 2.0.0

**Scope**
- Explicit support for all levels in the US and Canada: CAD or USD floors, sponsorship and work-status check, pay-transparency flag when a band is missing, North American resume norms.

**Token use**
- New output rules: answer first, no recaps, no full-JD restatement.
- Fixed four-line screen verdict format.
- Resume drafts show only the diff from the master.
- Reference files load only when a step needs them.
- Tracker replies list changed rows only.

**Screen**
- Reordered cheapest-first: hard exclusions, then geography and onsite, then comp.
- Added domain fit as its own step.
- Early-stage companies need named investors or named customers.
- Recent acquisitions or layoffs lower the tier instead of auto-skipping.
- Equity is additive, never a substitute for base.

**Resume**
- New `scripts/resume_builder.py`: auto-fit to page limit (spacing before type size), role headers kept with their first bullet, non-breaking contact line, text-layer validation for banned characters and regex phrases with word boundaries.
- Master resume as `resume_master.json`.
- Header title floor, locked positioning line, per-profile trim order, Skills variants by role archetype.
- "Draft" means text in chat. PDF only on request.

**Workflow**
- Outreach sequence: apply, IC peer question, design lead a few days later.
- Referral tracking with per-period limits.
- Passes list so declined companies are not resurfaced.
- Tracker in three piles (in progress, active, closed), sorted by last update, edited by string replacement.
- Ashby API fallback now includes compensation.

## 1.0.0

Initial release.
