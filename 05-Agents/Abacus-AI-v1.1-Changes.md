---
agent: "Abacus.AI"
version: "1.1"
date: "2026-09-11"
type: "Template Update"
files_changed:
  - "00-Templates/Session-Note.md"
  - "00-Templates/OPFMS-Client-Master.md"
  - "00-Templates/Client-Summary-Email.md"
tags: [changelog, agent-updates]
---

# Abacus.AI — Version 1.1 Changes

**Date:** September 11, 2026
**Type:** Template Update — Templater Plugin Integration
**Agent:** Abacus.AI

---

## Summary

Rewrote all three master templates to use proper **Templater plugin syntax**. Templates now auto-prompt for all required fields when a new note is created from them, replacing every placeholder automatically — including the YAML frontmatter, title, body, and client summary draft.

---

## What Changed

### Session-Note.md (full rewrite)
- Replaced all `{{CLIENT_NAME}}`, `{{date}}`, `{{session_number}}` etc. with Templater prompts
- Added Templater header block (`<%* ... -%>`) that collects:
  - Client Full Name (prompt)
  - Session Number (prompt, default "01")
  - Lesson Number (prompt, default "L01")
  - Lesson Title (prompt, optional)
  - Session Type (dropdown: Regular / Grievance / Catch-up / Review / Free-form with emoji labels)
- Auto-generates today's date in both YYYY-MM-DD and long format
- **Auto-renames the file** to `YYYY-MM-DD-Session-NN-LXX` format
- Auto-populates the client name in the Summary Draft section at the bottom
- Auto-fills YAML tags with the client name slug

### OPFMS-Client-Master.md (full rewrite)
- Added Templater header block that collects:
  - Client Full Name (prompt)
  - Client Email (prompt)
  - Client Mobile (prompt)
  - Date of Birth (prompt)
  - Job Title (prompt)
  - Organization (prompt)
  - Program Start Date (prompt, defaults to today)
  - Facilitator Name (prompt)
- **Auto-renames the file** to `OPFMS-FirstName-LastName` format
- Auto-populates the Participant Profile table with entered values
- Auto-fills all frontmatter fields

### Client-Summary-Email.md (full rewrite)
- Added Templater header block that collects:
  - Client Full Name (prompt)
  - Session Number (prompt)
  - Lesson Number (prompt)
  - Sent Via (dropdown: Email / WhatsApp with emoji labels)
- **Auto-renames the file** to `Summary-FirstName-LastName-Session-NN` format
- Auto-fills client greeting and all frontmatter

---

## How to Use the New Templates

### Prerequisite: Templater Plugin Setup
1. Settings → Community Plugins → Browse → install **Templater**
2. Settings → Templater:
   - Set **Template folder location** to `00-Templates`
   - Enable **Trigger Templater on new file creation**
   - (Optional) Set hotkey: `Alt+T` for "Templater: Open Insert Template Modal"

### Creating a New Session Note
1. Navigate to `01-Clients/[Client-Name]/Sessions/`
2. Create a new note (Ctrl/Cmd+N)
3. Open Command Palette → "Templater: Open Insert Template Modal"
4. Select `Session-Note`
5. Answer the prompts:
   - Client Full Name → e.g., `Habib BuJawdeh`
   - Session Number → e.g., `01`
   - Lesson → e.g., `L01`
   - Lesson Title → e.g., `Designing Your Life`
   - Session Type → pick from dropdown
6. File auto-renames to `2026-09-11-Session-01-L01.md`
7. All `<% ... %>` tags replaced with your answers throughout the note

### Creating a New Client OPFMS
1. Navigate to `01-Clients/`
2. Create a new subfolder for the client
3. Inside it, create a new note
4. Open Command Palette → "Templater: Open Insert Template Modal"
5. Select `OPFMS-Client-Master`
6. Answer the prompts (name, email, mobile, DOB, job title, org, start date, facilitator)
7. File auto-renames to `OPFMS-FirstName-LastName.md`
8. All fields pre-filled in both YAML and the Participant Profile table

### Creating a Client Summary
1. Navigate to the client's Sessions folder (or anywhere)
2. Create a new note
3. Open Command Palette → "Templater: Open Insert Template Modal"
4. Select `Client-Summary-Email`
5. Answer the prompts
6. File auto-renames to `Summary-ClientName-Session-NN.md`
7. Clean client-facing summary ready to finalize and send

---

## No Content Changes

Only the placeholder system was changed. All sections, fields, PFS scoring tables, forms selectors, intangibles registry, and workflow logic remain identical to v1.0.

---

*Version 1.1 — Templater integration complete*
