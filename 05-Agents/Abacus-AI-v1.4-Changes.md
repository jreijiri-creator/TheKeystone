---

agent: "[Abacus.AI](http://Abacus.AI)"\
version: "1.4"\
date: "2026-09-11"\
type: "New Automation — New Client Setup Wizard"\
files_added:

* "00-Templates/New-Client-Setup.md"\
  files_changed:

* "05-Agents/Abacus-AI.md"\
  tags: \[changelog, agent-updates\]

---

# [Abacus.AI](http://Abacus.AI) — Version 1.4 Changes

**Date:** September 11, 2026\
**Type:** New Automation — New Client Setup Wizard\
**Agent:** [Abacus.AI](http://Abacus.AI)

---

## Summary

Added `New-Client-Setup.md` — a single Templater script that creates the complete client folder structure AND the full OPFMS note in one trigger. No manual folder creation needed. The script self-destructs after setup is complete.

---

## How It Works

### Trigger

`Cmd+P` → "Templater: Create new note from template" → select **`New-Client-Setup`**

### What It Does (in sequence)

**Step 1 — Collects all info upfront (one pass of prompts):**

* Client First Name

* Client Last Name

* Email

* Mobile

* Date of Birth

* Job Title

* Organization / Company

* Program Start Date (defaults to today)

* Facilitator Name

**Step 2 — Creates the folder structure:**

```
01-Clients/FirstName-LastName/
├── Sessions/
└── Documents/
```

**Step 3 — Generates the full OPFMS note:**

* All YAML frontmatter pre-filled from prompts

* Participant Profile table pre-filled

* All sections ready for manual completion (personality, intangibles, wheel of life, etc.)

* Tags: `client`, `EPL12`, `ClientName`, `the-keystone-group`

* File named: `OPFMS-FirstName-LastName.md`

**Step 4 — Opens the new OPFMS note directly**

**Step 5 — Self-destructs the temporary setup note** (leaves no trace)

---

## What the Wizard Does NOT Do

These still require manual input after setup:

* Personality Profile (run assessment first)

* Win-Win Challenges (discussion with client)

* Wheel of Life baseline scores

* Intangibles #1–3 (client co-defines scale levels)

* Important Facilitator Notes

Session notes are created individually per session (by design).

---

## Technical Notes

* Uses `app.vault.createFolder()` for folder creation (silent fail if folder exists — safe to re-run)

* Uses `tp.file.create_new()` with inline content string (no sub-template call needed)

* Saves setup file path to `setupFilePath` BEFORE switching focus, then deletes it after

* The OPFMS content is a JavaScript template literal — all `${variable}` references resolve at runtime

* Located at: `00-Templates/New-Client-Setup.md`

---

_Version 1.4 — New Client Setup Wizard added_