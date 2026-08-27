# Product Design Job Search Workflow

A Claude skill that screens job postings against your actual criteria instead of generic advice.
Built for product designers at any level. The thresholds shift depending on where you are in your career, and the intake asks accordingly.

## What it does

- **Interviews you first.** Level, comp floor, geography, days in office, dealbreakers. Writes them into a profile it reuses.
- **Screens postings.** Paste a link or the job text. You get a yes or a skip with the failing criterion named.
- **Tailors your resume.** Reordering and re-cutting, never inventing. Includes the rule about never claiming a number you cannot defend in an interview.
- **Decides on cover letters.** Writes one only when there is a real hook, and says so when there is not.
- **Keeps a tracker.** One markdown file, updated as responses come in.

Also includes fetch workarounds for job boards that block direct access, including Ashby, Apple, and Workday.

## Install

1. Download `product-design-job-search-workflow.zip` from this repo.
2. In Claude, go to **Customize → Skills**, click **+**, then **+ Create skill**, and upload the zip.
3. Make sure **code execution and file creation** is enabled in settings. If it is off, the Skills menu is greyed out.
4. Start a **new** conversation. Claude reads skills at session start, so it will not appear in a chat that was already open.

## Getting started

Open a new chat and say:

> Set up my job search

Intake takes about ten minutes. Have your resume handy, since most of the profile gets drafted from it and you just correct the draft.

## Run it inside a Project

Your criteria get saved to a file called `job-search-profile.md`. For that to persist across conversations, work inside a Claude Project and keep the file there. Without a Project, intake runs again every time.

## What's in here

```
SKILL.md                      the workflow: the screen, tiers, cover letter policy, tracker
references/intake.md          the first-run interview and level calibration
references/profile-schema.md  structure of the profile file
references/resume-system.md   tailoring rules and the PDF build
references/fetch-notes.md     job board fetch behavior
```

Read `SKILL.md` before installing. It is plain text and it contains no scripts. Worth doing with any skill that asks about your salary.
