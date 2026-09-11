<%*
const clientName = await tp.system.prompt("Client Full Name");
const sessionNum = await tp.system.prompt("Session Number (e.g., 01)", "01");
const lessonNum = await tp.system.prompt("Lesson (e.g., L02 — or type NONE)", "L01");
const lessonTitle = await tp.system.prompt("Lesson Title (leave blank if no lesson)", "");
const sessionType = await tp.system.suggester(
  ["🟢 Regular", "🔴 Grievance", "🔁 Catch-up", "🔍 Review", "⚡ Free-form"],
  ["Regular", "Grievance", "Catch-up", "Review", "Free-form"]
);
const facilitator = await tp.system.prompt("Facilitator Name", "");
const today = tp.date.now("YYYY-MM-DD");
const todayLong = tp.date.now("MMMM DD, YYYY");
const slug = clientName.replace(/ /g, "-");
await tp.file.rename(`${today}-Session-${sessionNum}-${lessonNum}`);
-%>
---
client_name: "<% clientName %>"
session_number: <% sessionNum %>
session_date: "<% today %>"
lesson_covered: "<% lessonNum %>"
lesson_title: "<% lessonTitle %>"
session_type: "<% sessionType %>"
duration_min: 
facilitator: "<% facilitator %>"
pfs_score: 
tags: [session, <% slug %>, the-keystone-group]
---

# Session <% sessionNum %> — <% clientName %>

> **Date:** <% todayLong %> | **Lesson:** <% lessonNum %> — <% lessonTitle %> | **Type:** <% sessionType %>

---

## ⏮️ Carry-Forward from Previous Session

> *Review these BEFORE the session starts. Check off what was completed.*

### Open Action Steps (from last session):
- [ ] 
- [ ] 
- [ ] 

### Unfinished Assignments:
- [ ] 
- [ ] 

### Ongoing Goals Not Yet Achieved:
- [ ] 
- [ ] 

### Facilitator Reminders:
*(Things to bring up, check on, or be aware of this session)*

---

## 🌟 Intangible Check-In

> *Score at beginning or end of session. If client wants to improve, add a goal below.*

| Intangible | Last Score | Today's Score | Δ | Goal for Next Week? |
|---|---|---|---|---|
| [Intangible 1] | | | | |
| [Intangible 2] | | | | |
| [Intangible 3] | | | | |

**Intangible Goals Added This Session:**
- 

---

## 📝 Session Notes

> *Free-form coaching notes during the session — ideas discussed, brainstorm outputs, client statements, observations.*

### Key Discussion Points:

### Breakthroughs / Insights:

### Challenges Raised:

### Ideas Brainstormed:

### Coach Observations:

---

## 🤖 AI-Derived Action Steps

> **How this works (manual process — not automatic):**
> 1. Download your Zoom or Fathom transcript after the session
> 2. Paste a relevant excerpt below (the full transcript or a section)
> 3. Copy the transcript + the instruction line below → paste into Abacus.AI, Claude, or ChatGPT
> 4. Instruction to give the AI: *"From the transcript below, extract ONLY concrete action steps or commitments the client or coach made. List them as bullet points. Nothing else."*
> 5. Paste the AI's response into "Extracted Action Steps" below
> 6. **Do NOT send the transcript to the client** — only the extracted action steps go into the summary

**Transcript Excerpt (paste here):**
```
[PASTE TRANSCRIPT EXCERPT HERE]
```

**Extracted Action Steps:**
- 
- 
- 

---

## 🎯 Goals Set This Session

### Personal Goals:
- [ ] 
- [ ] 
- [ ] 

### Business / Professional Goals:
- [ ] 
- [ ] 
- [ ] 

### Intangible Goals:
- [ ] 
- [ ] 

### Carry-Forward from Previous (still active):
- [ ] 
- [ ] 

---

## 📋 PFS Scoring

> *Complete ONLY if a lesson chapter was covered this session.*

| Category | Max | Score | Notes |
|---|---|---|---|
| Application & Action | 10 | | |
| Reading & Listening (6 reps) | 10 | | |
| Best Idea (5 idea + 5 applied) | 10 | | |
| Business Goals Attainment | 10 | | |
| Personal Goals Attainment | 10 | | |
| Intangible Goal Attainment | 10 | | |
| Satisfaction / Relevance of Chapter | 40 | | |
| **TOTAL** | **100** | | |

**PFS Interpretation:** 90-100 Exceptional · 75-89 Strong · 60-74 Good · 40-59 Moderate · <40 Low

**PFS Narrative:**
*(Client's main feedback on the lesson — what resonated, what didn't)*

---

## 📦 Next Session Assignment Selector

**Lesson for Next Session:**
- [ ] Lesson ____ : ____________________ (same — not completed)
- [ ] Lesson ____ : ____________________ (advancing)
- [ ] Free-form / No lesson

**Forms to Assign:**

| Form Code | Form Name | Assign? | Notes |
|---|---|---|---|
| M020 | PFS — Participant Feedback | [ ] | |
| M021 | Action Steps Log | [ ] | |
| M022 | Emotional Intelligence Self-Evaluation | [ ] | |
| P012 | Personal Future Description | [ ] | |
| P080 | Business Future Description | [ ] | |
| P011 | Master Dream List | [ ] | |
| M002 | Bi-Weekly Goals Sheet | [ ] | |
| A029 | Article: Why War | [ ] | |
| *(other)* | | [ ] | |

**Audio/Box Link for Next Lesson:**
- Link: 

---

## 📤 Client Summary Draft

> *Review, finalize, and copy to send. Do NOT include transcript or raw coaching notes.*

---

Hello <% clientName %>,

It was great connecting with you today. Here is a summary of our session and what we've agreed on for the coming week.

**Session Highlights:**
*(2–3 sentence recap — fill in)*

---

### ✅ Your Goals for This Week

**Personal:**
- 
- 

**Professional:**
- 
- 

**Intangible:**
- 

---

### 📚 Your Assignment for Next Session

Please read and listen to **Lesson ___: [Title]** for a combined total of **6 repetitions**.

Forms to complete:
1. **M020** — Participant Feedback Sheet (PFS)
2. **M021** — Action Steps Log
3. *(add others as selected above)*

Lesson audio: [Box Link]

---

### 💬 Closing Note

*(Personal motivational closing — fill in)*

Looking forward to our next session.

Positively,
<% facilitator %>
The Keystone Group

---

*"If you are not making the progress you would like to make and are capable of making, it is merely because your goals are not clearly defined." — Paul J. Meyer*

---

*Note created: <% today %>*

---

## ✅ End-of-Session Checklist

> *Work through this before closing the note. Top to bottom.*

- [ ] **Intangible scores** filled in for all 3 intangibles
- [ ] **Goals** section complete — personal, professional, intangible, carry-forward
- [ ] **PFS score** filled in (if a lesson was covered) and recorded in OPFMS Session Log
- [ ] **Assignment Selector** checked — next lesson chosen, forms ticked
- [ ] **AI Action Steps** — transcript pasted and action steps extracted
- [ ] **Client Summary Draft** finalized at the bottom of this note
- [ ] **OPFMS Tangible Tracking** updated (W__ column) with today's PFS score and attendance
- [ ] **Client Summary sent** to client (email or WhatsApp)
- [ ] **GitHub Sync pushed** — Command Palette → "GitHub Sync: Push to remote"
