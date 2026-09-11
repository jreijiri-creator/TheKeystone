---
agent: "Abacus.AI"
version: "1.3"
date: "2026-09-11"
type: "Folder Structure Enhancement"
files_changed:
  - "05-Agents/Abacus-AI.md"
tags: [changelog, agent-updates]
---

# Abacus.AI — Version 1.3 Changes

**Date:** September 11, 2026
**Type:** Folder Structure Enhancement
**Agent:** Abacus.AI

---

## Summary

Added a **Documents/** subfolder to each client's folder structure to provide a dedicated location for storing client-uploaded files, completed forms, attachments, and any other documents exchanged during coaching.

---

## What Changed

### Folder Structure Update

**Previous structure:**
```
01-Clients/
  └── [Client-Name]/
      ├── OPFMS-[Name].md
      └── Sessions/
```

**New structure:**
```
01-Clients/
  └── [Client-Name]/
      ├── OPFMS-[Name].md
      ├── Sessions/
      └── Documents/         # NEW — for uploaded files, forms, attachments
```

### Purpose of the Documents/ Folder

- **Store client-submitted forms** (filled PDFs of M020, M021, P012, etc.)
- **Archive email attachments** the client sends
- **Keep reference materials** specific to this client (articles, worksheets, custom assessments)
- **Organize session-related files** without cluttering the Sessions/ folder

### Updated Workflow: Creating a New Client

The "Creating a New Client" section in `Abacus-AI.md` now includes:

**Step 3:** Create subfolder: `01-Clients/[FirstName-LastName]/Documents/`

Full updated workflow:
1. Create folder: `01-Clients/[FirstName-LastName]/`
2. Create subfolder: `01-Clients/[FirstName-LastName]/Sessions/`
3. Create subfolder: `01-Clients/[FirstName-LastName]/Documents/` ← NEW
4. Inside the client folder, create a new note using Templater → insert `OPFMS-Client-Master` template
5. Answer all prompts
6. File auto-renames to `OPFMS-[FirstName-LastName].md`
7. Fill in remaining sections (personality, intangibles, facilitator notes)

---

## Files Changed

- `05-Agents/Abacus-AI.md` — Updated:
  - Folder Structure diagram (added Documents/ folder)
  - Creating a New Client workflow (added step 3)
  - Change Log (added v1.3 entry)

---

## Action for Existing Clients

If you have existing clients in your vault (e.g., Joanna Abou Jaoudeh, Habib BuJawdeh), you can manually add a `Documents/` folder to their existing structure:

1. Navigate to `01-Clients/[Client-Name]/`
2. Create a new folder called `Documents`
3. Move any existing client files (PDFs, attachments) into it

This is optional — the folder structure will automatically be correct for all new clients moving forward.

---

*Version 1.3 — Documents folder added to client structure*
