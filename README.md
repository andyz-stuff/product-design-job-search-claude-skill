# Product Design Job Search Workflow

A Claude skill that screens job postings against your actual criteria instead of generic advice.

Most of the waste in a job search happens before you apply, on roles that were never going to work. This runs a seven-step screen on every posting and stops at the first failure, so a role that fails on comp never gets an hour of resume tailoring.

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

A greeting will not trigger it. Skills load when the request matches, and a description that fired on "hi" would fire on everything. Pasting a job link works too.

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

## Notes

This came out of a real search, then had the personal specifics stripped out. Nothing in it knows anything about a particular person until it asks you.

Issues and corrections welcome. The screen will be wrong for some people and some roles, and knowing where is more useful than agreement.
