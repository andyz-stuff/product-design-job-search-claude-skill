# Product Design Job Search Workflow

A Claude skill that screens job postings against your real criteria, then tailors your resume only for roles that pass.

Most of the waste in a job search happens before you apply, on roles that were never going to work. This runs a seven-step screen on every posting and stops at the first failure, so a role that fails on comp never gets an hour of tailoring.

For UX and product designers at any level, junior to principal, searching in the US and Canada.

## What it does

- **Interviews you once.** Level, comp floor, geography, days in office, dealbreakers. Saves them to a profile it reuses.
- **Screens postings.** Paste a link or the job text. You get a four-line verdict: apply (with tier) or skip (with the failing step).
- **Tailors your resume.** Shows only what changed from your master resume. Reorders and re-cuts, never invents.
- **Builds the PDF.** A script that auto-fits to your page limit and checks the text layer for banned characters and phrases before you send it.
- **Decides on cover letters.** Writes one only when there is a real hook.
- **Keeps a tracker.** One markdown file in three piles: in progress, active, closed.
- **Plans outreach.** Apply, then a peer question to an IC designer, then the design lead a few days later.

## Install

1. Download `product-design-job-search-workflow.zip` from this repo.
2. In Claude, go to **Customize → Skills**, click **+**, then **+ Create skill**, and upload the zip.
3. Turn on **code execution and file creation** in settings. If it is off, the Skills menu is greyed out.
4. Start a **new** conversation. Skills load at session start.

**Updating from v1:** delete the old skill in Customize → Skills, then upload the new zip. Your `job-search-profile.md` keeps working. v2 reads a few new optional sections (passes, referrals, resume settings); intake will offer to add them.

## Getting started

Open a new chat inside a Claude Project and say:

> Set up my job search

Pasting a job link works too. A greeting will not trigger it.

Intake takes about 10 minutes. Have your resume ready; most of the profile is drafted from it and you correct the draft.

## Use a Project

Your criteria live in `job-search-profile.md`, your master resume in `resume_master.json`, and your tracker in `job-tracker-YYYY-MM-DD.md`. Keep all three in a Claude Project so they persist. Without a Project, intake runs every time.

## Files

```
product-design-job-search-workflow/
  SKILL.md                     the screen, output rules, tiers, workflow
  references/intake.md         first-run interview, level calibration
  references/profile-schema.md profile structure
  references/resume-system.md  tailoring rules, build, verification
  references/tracker.md        tracker format and edit rules
  references/fetch-notes.md    job board fetch behavior
  scripts/resume_builder.py    PDF generator and validator
```

`scripts/resume_builder.py` is the only code. It uses ReportLab, reads your content JSON, and writes a PDF. Its one network call downloads the open-source Inter font from its GitHub release; it falls back to Helvetica if that is blocked. Read it before installing, as with any skill that handles your salary.

## Notes

Built from a real search, with personal details removed. It knows nothing about you until intake.

Issues and corrections welcome. The screen will be wrong for some people and some roles, and knowing where is more useful than agreement.
