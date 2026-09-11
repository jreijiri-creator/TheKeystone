---
agent: "Abacus.AI"
purpose: "System context and instructions for AI assistants working on The Keystone coaching vault"
last_updated: "2026-09-11"
version: "1.0"
tags: [agent-instructions, system-context, preferences]
---

# Abacus.AI — System Context & Instructions

> **Purpose:** This file captures all design decisions, user preferences, workflow patterns, and structural rules for The Keystone Group's Obsidian-based coaching management system. Any AI assistant working on this vault should read this file first to understand the system architecture and user requirements.

---

## 📋 Table of Contents

1. [Project Overview](#project-overview)
2. [User Requirements & Preferences](#user-requirements--preferences)
3. [System Architecture](#system-architecture)
4. [Workflow Patterns](#workflow-patterns)
5. [PFS Scoring Methodology](#pfs-scoring-methodology)
6. [Template Usage & Philosophy](#template-usage--philosophy)
7. [Forms System](#forms-system)
8. [Client Management Approach](#client-management-approach)
9. [Future Roadmap](#future-roadmap)
10. [Technical Notes](#technical-notes)

---

## Project Overview

### Context
The Keystone Group is a leadership and legacy development coaching practice that delivers the **Effective Personal Leadership (EPL12)** program — a 12-lesson structured curriculum developed by Leadership Management International (LMI).

### The Problem We Solved
Previously, client tracking was done in Apple Numbers (`.numbers` files), which:
- Required credits/licenses to access
- Was not accessible to AI assistants for automation
- Lacked integration with other tools (Obsidian, transcripts, etc.)
- Was difficult to query across multiple clients

### The Solution
A complete Obsidian vault system that:
- Uses plain Markdown files (zero-cost, AI-accessible, future-proof)
- Integrates with GitHub for version control and sync
- Connects with Obsidian for note-taking and client management
- Supports AI-assisted workflows (transcript parsing, goal extraction)
- Scales to ~20 active clients
- Prepares for future automation (Zoom/Fathom transcript integration, WhatsApp summary links)

---

## User Requirements & Preferences

### Core Requirements (from initial conversation)

1. **Zero-cost system after setup** — no recurring licenses or subscriptions
2. **AI-accessible data** — all client data should be readable/writable by AI assistants
3. **Obsidian integration** — native note-taking environment the user already uses
4. **Adaptive session workflow** — sessions are NOT always sequential (client may skip lessons, have grievances, incomplete assignments)
5. **Carry-forward logic** — new session notes should automatically pull open action steps and unfinished assignments from previous session
6. **Client capacity** — system must handle approximately 20 active clients simultaneously

### Intangibles Tracking Requirements

**Definition:** Intangibles are behavioral or attitudinal habits the client wants to develop (e.g., "Freedom," "Security," "Confidence").

**Process:**
1. Coach and client identify a specific behavior/attitude together
2. Client defines the scale: what +10, +5, 0, -5, -10 mean FOR THAT SPECIFIC INTANGIBLE
3. Scoring happens at the beginning OR end of each session
4. If the client wants to improve, they set a goal for the next week
5. That goal gets added to their weekly goals list

**Key Point:** Each intangible has a CUSTOM scale definition unique to that client and that behavior. The scale is NOT standardized across clients or intangibles.

**Types:**
- **Intangibles:** Behaviors, attitudes, feelings — scored on -10 to +10 scale with custom definitions
- **Tangibles:** Measurable indicators — can be numbers (weight, reps), checkmarks (✓/✗), or yes/no

### Session Workflow Requirements

**During Session:**
- Facilitate brainstorming and idea generation with client
- Jot down goals and action steps in real-time
- All reading and discussions should generate goals and action steps
- Review goals/action steps with client at END of session before finalizing

**End of Session:**
- Choose the lesson/assignment for next time from a dropdown/selector (not always sequential)
- Pre-draft the client summary email/note
- Send or share summary (future: as a WhatsApp link to a markdown file)

**Between Sessions:**
- Client completes assignments (forms, reading, listening)
- Coach does NOT need the full transcript — only AI-extracted action steps from Zoom/Fathom transcript

### PFS Scoring Requirements

**Critical:** PFS uses a **unified 100-point score** (not separate scores per form field).

**Breakdown (total = 100):**
- Application & Action: 10 pts
- Reading & Listening (6 reps target): 10 pts
- Best Idea (5 idea + 5 applied): 10 pts
- Business Goals Attainment: 10 pts
- Personal Goals Attainment: 10 pts
- Intangible Goal Attainment: 10 pts
- Satisfaction from Chapter (relevance to client's situation): 40 pts

**Scoring Legend:** The legend above must be included at the end of EVERY PFS form and in the session note PFS scoring table.

### Forms & Assignments

**All LMI forms must be:**
1. Converted to fillable Markdown fields
2. Stored in `02-Forms-Repository/`
3. Available via dropdown/selector in session notes
4. Scored using the unified 100-point scale

**Current forms:**
- M020: Participant Feedback Sheet (PFS)
- M021: Action Steps Log
- M022: Emotional Intelligence Self-Evaluation
- P012: Personal Future Description
- P080: Business Future Description
- P011: Master Dream List (ongoing)
- M002: Bi-Weekly Goals Sheet
- A029: "Why War" article (supplementary reading)

### Client-Facing Outputs

**Requirements:**
- Email-ready markdown format
- Eventually: send as a WhatsApp link to the markdown file (not yet implemented)
- Must include: session highlights, goals for the week, assignment details, forms list, audio link, motivational closing quote

---

## System Architecture

### Folder Structure

```
Keystone-Obsidian-Vault/
├── 00-Templates/              # Master templates for duplication
│   ├── OPFMS-Client-Master.md
│   ├── Session-Note.md
│   └── Client-Summary-Email.md
├── 01-Clients/                # One subfolder per client
│   └── [Client-Name]/
│       ├── OPFMS-[Name].md    # Client master sheet
│       └── Sessions/          # All session notes
├── 02-Forms-Repository/       # All LMI forms as markdown
├── 03-Assignments/            # Per-lesson assignment templates
├── 04-Resources/              # Guides, scoring references
├── 05-Agents/                 # AI context and instructions (this file)
└── README.md
```

### File Naming Conventions

- **Client OPFMS:** `OPFMS-[FirstName-LastName].md`
- **Client folder:** `[FirstName-LastName]/`
- **Session notes:** `YYYY-MM-DD-Session-XX-LXX.md` (date, session number, lesson)
- **Forms:** `[FormCode]-[Form-Name].md` (e.g., `M020-PFS-Participant-Feedback.md`)

### Version Control (GitHub)

- **Repo:** `https://github.com/jreijiri-creator/TheKeystone.git`
- **Branch:** `main`
- **Sync method:** GitHub Sync plugin in Obsidian
- **User:** `jreijiri-creator`

**Workflow:**
1. AI makes edits in `/home/ubuntu/github_repos/TheKeystone/`
2. AI commits and pushes to GitHub
3. User pulls in Obsidian via Command Palette → "GitHub Sync: Pull from remote"

---

## Workflow Patterns

### Creating a New Client

1. Duplicate `00-Templates/OPFMS-Client-Master.md`
2. Create folder: `01-Clients/[FirstName-LastName]/`
3. Create subfolder: `01-Clients/[FirstName-LastName]/Sessions/`
4. Rename duplicated template: `OPFMS-[FirstName-LastName].md`
5. Fill in YAML frontmatter
6. Fill in Participant Profile section
7. Run personality assessment → fill Personality Profile
8. Define intangibles together with client (custom scale definitions)

### Starting a New Session

1. Open client's `OPFMS-[Name].md` → review Session Log for context
2. Duplicate `00-Templates/Session-Note.md`
3. Rename: `YYYY-MM-DD-Session-XX-LXX.md`
4. Move into `01-Clients/[Name]/Sessions/`
5. Fill **Carry-Forward** section from previous session note
6. Update intangible scores at start or end of session
7. Take notes during session
8. At end: choose assignment from selector, draft client summary
9. Copy summary → finalize → send/share

### Processing AI Transcripts

**Current Workflow:**
1. Download Zoom/Fathom transcript after session ends
2. Paste excerpt into session note's "AI-Derived Action Steps" section
3. Ask AI: "From the transcript below, extract ONLY concrete action steps or commitments. List as bullets."
4. Paste extracted action steps into the session note
5. Incorporate into goals list

**Future (when webhook available):**
- Auto-populate action steps field from transcript API

### Scoring PFS

**When:** After client completes lesson and submits M020 form.

**Process:**
1. Review client's M020 form submission
2. Fill PFS Scoring table in session note
3. Apply scoring legend (see PFS Scoring Methodology section)
4. Record total `/100` in session log
5. Update client's OPFMS tangible tracking table

---

## PFS Scoring Methodology

### Unified 100-Point Scale

| Category | Max | How to Score |
|---|---|---|
| **Application & Action** | 10 | Did client complete action steps in M021? Full = 10, Partial = 5, None = 0 |
| **Reading & Listening** | 10 | Combined reps target = 6. Score = (actual / 6) × 10, rounded |
| **Best Idea** | 10 | 5 pts for identifying idea + 5 pts for applying (or planning to apply) it |
| **Business Goals Attainment** | 10 | Self-assessed vs. goals set last session. Full = 10, Partial = 5-7, None = 0 |
| **Personal Goals Attainment** | 10 | Self-assessed vs. goals set last session. Full = 10, Partial = 5-7, None = 0 |
| **Intangible Goal Attainment** | 10 | Based on intangible score movement toward goal. Reached = 10, Progress = 5-8, None = 0 |
| **Satisfaction / Relevance** | 40 | How relevant was this chapter to client's current situation? Self-reported. Range: 0-40 |

### Interpretation Benchmarks

| Total Score | Interpretation |
|---|---|
| 90–100 | Exceptional engagement — celebrate and anchor |
| 75–89 | Strong — acknowledge and build momentum |
| 60–74 | Good — identify what held back full engagement |
| 40–59 | Moderate — explore blockers; adjust approach |
| Below 40 | Low — significant follow-up required; check motivation |

---

## Template Usage & Philosophy

### OPFMS Client Master Template

**Purpose:** Single source of truth for each client. Contains everything the coach needs to know about a client across their entire program.

**Key Sections:**
- Participant Profile (contact info, job, organization)
- Personality Profile (Analyzer/Supportive/Enterpriser/Promoter assessment)
- Win-Win Challenges (core issues client is addressing)
- Personal Leadership Evaluation (baseline → current scores)
- Wheel of Life (6 pillars + scores)
- **Intangibles Registry** (custom scale definitions + scoring history per intangible)
- Tangible Indicators Tracking (weekly tracking table)
- Session Log (all sessions with dates, lessons, PFS scores, outcomes)
- Important Facilitator Notes (patterns, quotes, what NOT to do with this client)

**Design Philosophy:**
- All client context in ONE file
- Easy to review before a session
- Longitudinal tracking (patterns emerge over time)

### Session Note Template

**Purpose:** Real-time workspace during a session + deliverable generator.

**Key Features:**
- **Carry-Forward Section:** Auto-populated from previous session (open action steps, unfinished assignments, ongoing goals)
- **Adaptive:** Not tied to a specific lesson (can choose any lesson or none)
- **Intangible Check-In:** Score at start/end, set goals if needed
- **AI Transcript Section:** Paste excerpt, extract action steps
- **Goals Set This Session:** Personal, Business, Intangible, Carry-Forward
- **PFS Scoring Table:** Unified 100-point score with legend
- **Assignment Selector:** Dropdown-style table to choose forms for next session
- **Client Summary Draft:** Pre-filled at bottom, ready to copy/send

**Design Philosophy:**
- One note = one session's full context
- Coach can work top-to-bottom during session
- Outputs (summary, goals, PFS) generated in same note

### Client Summary Email Template

**Purpose:** Clean, client-facing note with goals and assignments.

**Design Philosophy:**
- No coach notes or internal observations
- Positive, encouraging tone
- Clear next steps
- Future: shareable as WhatsApp link

---

## Forms System

### Repository Structure

All forms live in `02-Forms-Repository/` as fillable markdown templates.

### Form Conversion Standards

When converting PDF forms to markdown:
1. Preserve all fields and questions
2. Use markdown tables for multi-item scales
3. Include scoring legends where applicable (especially PFS)
4. Add YAML frontmatter with form metadata
5. Keep copyright notices intact (adapted for markdown)

### Current Forms Inventory

| Code | Name | Lesson | Type |
|---|---|---|---|
| M020 | Participant Feedback Sheet (PFS) | Each | Scoring + reflection |
| M021 | Action Steps Log | Each | Habit tracker |
| M022 | Emotional Intelligence Self-Evaluation | L02 | Self-assessment (20 items) |
| P012 | Personal Future Description | L02 | Vision exercise |
| P080 | Business Future Description | L08 | Vision exercise |
| P011 | Master Dream List | L01+ | Ongoing list |
| M002 | Bi-Weekly Goals Sheet | Each | Goal tracker |
| A029 | "Why War" Article | L02-03 | Supplementary reading |

---

## Client Management Approach

### Scale
- Target capacity: **~20 active clients**
- Session frequency: typically bi-weekly (every 2 weeks)
- Program duration: 12 lessons over ~6 months

### Privacy & Security
- **All client data is confidential**
- GitHub repo should remain **private**
- When sharing examples, anonymize or use existing example (Joanna)

### Facilitator Style Notes

From the OPFMS structure, we know the facilitator tracks:
- "What NOT to do with this participant"
- "How to care" (individualized support approach)
- "People to network with this participant"
- Observed patterns and important quotes

**This suggests a highly personalized, relationship-driven coaching model.**

---

## Future Roadmap

### Near-Term (Next 3 Months)

1. **Template Placeholder System**
   - Decide: simple manual placeholders vs. full Templater automation
   - Update all templates accordingly

2. **Dataview Queries**
   - Build queries for: active clients list, recent sessions, low PFS scores, upcoming sessions

3. **Additional Forms**
   - Convert remaining LMI forms as they come up in lessons 3-12

4. **Habib BuJawdeh Client**
   - Complete OPFMS setup for the newly created client

### Mid-Term (3-6 Months)

1. **WhatsApp Link Sharing**
   - Generate shareable markdown links for client summaries
   - Options: Obsidian Publish (paid) or self-hosted static site

2. **Transcript Integration**
   - Automate action step extraction from Zoom/Fathom
   - Webhook or API integration

3. **Dashboard View**
   - Create a vault homepage with Dataview dashboards
   - At-a-glance view of all 20 clients

### Long-Term (6+ Months)

1. **Automated Session Prep**
   - AI generates pre-session briefing from previous notes
   - Auto-populated carry-forward section

2. **Goal Tracking Automation**
   - Cross-note goal status tracking
   - Alert when goals are overdue or incomplete

3. **Analytics**
   - PFS trends over time
   - Intangible progress visualization

---

## Technical Notes

### GitHub Sync Setup

**Plugin:** GitHub Sync (Obsidian Community Plugin)

**Initial Setup Commands (run in terminal at vault location):**
```bash
git init
git remote add origin https://github.com/jreijiri-creator/TheKeystone.git
git fetch origin
git branch -M main
git reset --hard origin/main
```

**Ongoing Workflow:**
- AI edits files in `/home/ubuntu/github_repos/TheKeystone/`
- AI commits + pushes to GitHub
- User pulls in Obsidian: Command Palette → "GitHub Sync: Pull from remote"

### Recommended Obsidian Plugins

| Plugin | Purpose | Essential? |
|---|---|---|
| **Dataview** | Query notes, build dashboards | Yes |
| **Templater** | Auto-fill templates (if we use advanced mode) | Optional |
| **Calendar** | Visual session calendar | Nice-to-have |
| **GitHub Sync** | Push/pull to GitHub | Yes |

### File Encoding & Line Endings
- **Encoding:** UTF-8
- **Line endings:** LF (Unix-style)
- **No BOM**

### Backup Strategy
- **Primary:** GitHub repo (version controlled)
- **Secondary:** iCloud Drive (where vault lives)
- **Frequency:** Real-time (GitHub Sync after each session)

---

## Change Log

| Date | Version | Changes |
|---|---|---|
| 2026-09-11 | 1.0 | Initial creation — captured all requirements from vault build conversation |
| 2026-09-11 | 1.1 | Rewrote all three templates with Templater plugin syntax |
| 2026-09-11 | 1.2 | Fixed template issues: removed PDF/DOCX from 00-Templates, added facilitator prompt to Session-Note and Client-Summary-Email, added company tag (the-keystone-group) to all templates, clarified AI-Derived Action Steps workflow, added End-of-Session Checklist |

---

## Instructions for AI Assistants

When working on this vault in future conversations:

1. **Always read this file first** before making structural changes
2. **Preserve the unified 100-point PFS scoring system** — do not revert to separate scores
3. **Respect the intangibles custom scale philosophy** — each intangible has unique definitions
4. **Maintain the carry-forward logic** in session notes
5. **Keep the adaptive session workflow** — never assume lessons are sequential
6. **Update this file** when user requirements change or new patterns emerge
7. **Test changes** by pushing to GitHub and confirming user can pull successfully
8. **Create a changelog note after every edit** to the `05-Agents/` folder — format: `[AGENT-NAME]-v[X.X]-Changes.md` documenting what changed and why

---

*The Keystone Group · Leadership & Legacy Development*
*System designed and built: September 2026*
