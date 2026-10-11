# Meet Class Companion

A Chrome extension for Google Meet classes that gives students a private note-taking workspace and, only if they agree, gives professors an automatic attention report.

## What it does

**For students**
- Take notes in a side panel without leaving the Meet tab, with optional timestamps.
- Capture slides with an explicit button and a crop step. Nothing is captured automatically.
- Export notes as Markdown or PDF. Notes and screenshots stay on the student's computer and are never uploaded.

**For professors**
- Create a class on a web dashboard and share a class code with students.
- See a report for each meeting: time on the class tab, time taking notes, tab and window switches, and answers to the "Are you still there?" check.
- Time spent taking notes appears as "taking notes", not as an unexplained gap.

## Built around consent

- Students see exactly what is logged, who sees it, and what the "Are you still there?" popup does before anything is recorded.
- Declining means no tracking. The only record is one line: "No tracking record. Student declined tracking."
- A badge in the corner of Meet shows the current state, and students can stop sharing or edit their details at any time.
- The log records timestamps and activity states only. It never records keystrokes, note content, screenshots, or which other sites or apps are used.

## How it works

Manifest V3 extension (content script, service worker, side panel). Events are saved locally first, then uploaded to Firebase (Firestore) in the background. The professor dashboard is a static page on Firebase Hosting. Events are tamper-evident (hash-chained) and cannot be edited after upload.

## Setup

- Students and professors: see `INSTALL-GUIDE.txt`.
- Firebase project setup: see `docs/SETUP-FIREBASE.md`.

## Limitations

It only monitors desktop Chrome, and a determined student can switch it off or use another device. Identity is self-declared, and the numbers are evidence to discuss, not a verdict. Logging students usually needs institutional approval.

## Status

Work in progress. Core logic is covered by automated tests (`npm test`); live testing against Google Meet and Firebase is ongoing.
