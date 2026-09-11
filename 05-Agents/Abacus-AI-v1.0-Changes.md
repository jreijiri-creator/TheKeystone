---
agent: "Abacus.AI"
version: "1.0"
date: "2026-09-11"
type: "Initial Creation"
files_changed: ["Abacus-AI.md"]
tags: [changelog, agent-updates]
---

# Abacus.AI — Version 1.0 Changes

**Date:** September 11, 2026  
**Type:** Initial Creation  
**Agent:** Abacus.AI

---

## Summary

Created the complete AI context and system documentation file (`Abacus-AI.md`) that captures all design decisions, user preferences, and operational guidelines for The Keystone Group's Obsidian coaching vault.

---

## What Was Created

### New Files
- `05-Agents/Abacus-AI.md` — Main system documentation (476 lines)

### Purpose
This file serves as the **living system documentation** that any AI assistant should read before working on the vault. It ensures continuity across conversations and prevents loss of critical context.

---

## Key Content Sections

1. **Project Overview** — Context of the problem and solution
2. **User Requirements & Preferences** — All captured requirements from initial conversation
3. **System Architecture** — Folder structure, naming conventions, GitHub setup
4. **Workflow Patterns** — Step-by-step processes for new clients, sessions, transcript processing
5. **PFS Scoring Methodology** — Complete 100-point scoring breakdown with interpretation benchmarks
6. **Template Usage & Philosophy** — Design rationale for each template
7. **Forms System** — Conversion standards and current inventory
8. **Client Management Approach** — Scale, privacy, facilitator style notes
9. **Future Roadmap** — Near-term, mid-term, and long-term development plans
10. **Technical Notes** — GitHub sync setup, recommended plugins, backup strategy

---

## Critical Requirements Captured

### Intangibles System
- Custom -10 to +10 scales defined by each client
- Each intangible has unique meaning per behavior
- Scored at start or end of each session
- Progress drives weekly goal setting

### PFS Scoring
- **Unified 100-point system** (not separate scores)
- Breakdown: Application (10) + Reps (10) + Best Idea (10) + Business Goals (10) + Personal Goals (10) + Intangibles (10) + Satisfaction (40)
- Scoring legend must appear in every PFS form

### Session Workflow
- **Adaptive, not sequential** — lessons can be skipped, repeated, or chosen out of order
- **Carry-forward logic** — new sessions auto-pull open items from previous session
- Client capacity: ~20 active clients

### Technical Setup
- Zero-cost requirement after initial setup
- AI-accessible plain markdown files
- GitHub for version control and sync
- iCloud Drive for local storage

---

## Design Philosophy Principles

1. **Single Source of Truth** — Each client has ONE master OPFMS file
2. **Longitudinal Tracking** — Patterns emerge over time through consistent structure
3. **Relationship-Driven** — Facilitator tracks "what NOT to do", "how to care", important quotes
4. **Client-Facing Separation** — Internal notes never appear in client summaries
5. **Future-Proof** — Plain text, vendor-neutral, AI-accessible

---

## Instructions for Future Updates

When any AI assistant edits `Abacus-AI.md` or other files in `05-Agents/`:

1. Increment the version number in the main file's frontmatter
2. Update the `last_updated` date
3. Add entry to the Change Log table at bottom of main file
4. **Create a new changelog note** following this format: `Abacus-AI-v[X.X]-Changes.md`
5. Document what changed, why, and any new requirements or patterns

---

## Git Commit

**Commit message:** `Add AI context file: 05-Agents/Abacus-AI.md with full system documentation`  
**Branch:** `main`  
**Files added:**
- `05-Agents/Abacus-AI.md`
- `05-Agents/Abacus-AI.pdf` (auto-generated)
- `05-Agents/Abacus-AI.docx` (auto-generated)

---

## Next Steps

1. User will pull this file via GitHub Sync in Obsidian
2. User may edit to add corrections or additional preferences
3. When template placeholder system is decided (manual vs. Templater), update the roadmap section
4. As new patterns emerge from actual coaching sessions, document them in the main file

---

*Version 1.0 — Initial system documentation complete*
