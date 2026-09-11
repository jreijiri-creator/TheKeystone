---
agent: "Abacus.AI"
version: "1.5"
date: "2026-09-11"
type: "Navigation Fix — TOC Added to All Vault Files"
files_changed:
  - "00-Templates/Session-Note.md"
  - "00-Templates/OPFMS-Client-Master.md"
  - "00-Templates/Client-Summary-Email.md"
  - "01-Clients/Joanna-Abou-Jaoudeh/OPFMS-Joanna-Abou-Jaoudeh.md"
  - "02-Forms-Repository/M020-PFS-Participant-Feedback.md"
  - "02-Forms-Repository/M021-Action-Steps.md"
  - "02-Forms-Repository/M022-Emotional-Intelligence.md"
  - "02-Forms-Repository/P012-Personal-Future-Description.md"
  - "02-Forms-Repository/P080-Business-Future-Description.md"
  - "04-Resources/PFS-Scoring-Guide.md"
  - "04-Resources/Vault-Setup-Guide.md"
  - "03-Assignments/EPL12-L02-Assignment.md"
  - "03-Assignments/_Assignment-Template.md"
  - "05-Agents/Abacus-AI.md"
tags: [changelog, agent-updates]
---

# Abacus.AI — Version 1.5 Changes

**Date:** September 11, 2026
**Type:** Navigation Fix — TOC Added to All Vault Files
**Agent:** Abacus.AI

---

## Summary

User reported that internal heading links were not working (clicking did nothing). Root cause: Obsidian's Live Preview mode does not follow standard markdown `[text](#anchor)` links. Added `[[#Heading]]` format TOC navigation bars to all 13 content files in the vault. These links work in **both Live Preview and Reading View**.

Also discovered and repaired a corrupted `Session-Note.md` that contained changelog content instead of the template — restored cleanly from git history.

---

## What Changed

### Internal Link Format — Why It Matters

| Format | Live Preview | Reading View |
|---|---|---|
| `[text](#anchor)` (standard markdown) | ❌ Does nothing | ✅ Works |
| `[[#Heading Text]]` (Obsidian native) | ✅ Works | ✅ Works |

All TOCs in this vault now use the `[[#Heading Text]]` format.

### TOC Format

Each file received a navigation callout block placed immediately after the main title (H1), before the first section (H2). Format:

```markdown
> **📋 Quick Navigation**
> [[#Section One]] · [[#Section Two]] · [[#Section Three]]
```

Sections are separated by `·` for a compact single-line or two-line layout.

---

## Files Updated (13 total)

### Templates (3)
- **Session-Note.md** — 9 section links: Carry-Forward → Intangibles → Session Notes → AI Steps → Goals → PFS → Assignment Selector → Client Summary → Checklist
- **OPFMS-Client-Master.md** — 13 section links: full client master sheet navigation
- **Client-Summary-Email.md** — 3 section links (short file)

### Existing Client Files (1)
- **OPFMS-Joanna-Abou-Jaoudeh.md** — 12 section links matching actual headings in her file

### Forms Repository (5)
- **M020-PFS-Participant-Feedback.md** — 10 section links
- **M021-Action-Steps.md** — 6 section links
- **M022-Emotional-Intelligence.md** — 4 section links
- **P012-Personal-Future-Description.md** — 4 section links
- **P080-Business-Future-Description.md** — 4 section links

### Resources (2)
- **PFS-Scoring-Guide.md** — 3 section links
- **Vault-Setup-Guide.md** — 9 section links

### Assignments (2)
- **EPL12-L02-Assignment.md** — 6 section links
- **_Assignment-Template.md** — 6 section links

---

## Bug Fixed: Session-Note.md Corruption

On inspection, `Session-Note.md` was found to contain the content of `Abacus-AI-v1.2-Changes.md` instead of the actual session note template. Cause: a file write operation in a previous session wrote to the wrong path. The file was restored cleanly using `git show a937110:00-Templates/Session-Note.md`. No session notes already created for clients were affected — this was only the blank template.

---

## Rule Added to AI Instructions

Internal links in this vault must always use `[[#Heading Text]]` format, never `[text](#anchor)`. This applies to any new TOCs, cross-references, or navigation elements added in future sessions.

---

*Version 1.5 — TOC navigation added to all 13 vault files. Links now work in both Obsidian modes.*
