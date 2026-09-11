<%*
const clientName = await tp.system.prompt("Client Full Name (First Last)");
const clientEmail = await tp.system.prompt("Client Email", "");
const clientMobile = await tp.system.prompt("Client Mobile", "");
const clientDOB = await tp.system.prompt("Date of Birth (YYYY-MM-DD)", "");
const jobTitle = await tp.system.prompt("Job Title", "");
const organization = await tp.system.prompt("Organization / Company", "");
const startDate = await tp.system.prompt("Program Start Date (YYYY-MM-DD)", tp.date.now("YYYY-MM-DD"));
const facilitator = await tp.system.prompt("Facilitator Name", "");
const today = tp.date.now("YYYY-MM-DD");
const slug = clientName.replace(/ /g, "-");
await tp.file.rename(`OPFMS-${slug}`);
-%>
---
client_name: "<% clientName %>"
email: "<% clientEmail %>"
mobile: "<% clientMobile %>"
date_of_birth: "<% clientDOB %>"
job_title: "<% jobTitle %>"
organization: "<% organization %>"
program: "EPL12"
program_start_date: "<% startDate %>"
box_folder: ""
facilitator: "<% facilitator %>"
status: "Active"
total_sessions: 0
tags: [client, EPL12, <% slug %>, the-keystone-group]
---

# <% clientName %> — One Page Facilitation Management Sheet (OPFMS)

> **Program:** EPL12 | **Start:** <% startDate %> | **Facilitator:** <% facilitator %>
> **Status:** Active

---

## 👤 Participant Profile

| Field | Value |
|---|---|
| Name | <% clientName %> |
| Email | <% clientEmail %> |
| Mobile | <% clientMobile %> |
| Date of Birth | <% clientDOB %> |
| Job Title | <% jobTitle %> |
| Organization | <% organization %> |
| Box Folder | |

---

## 🧠 Personality Profile

### Analyzer / Supportive / Enterpriser / Promoter Assessment

| Role | Challenges | Strengths | Things to Work On |
|---|---|---|---|
| **Analyzer** | | | |
| **Supportive** | | | |
| **Enterpriser** | | | |
| **Promoter** | | | |

**Dominant Role:**
**Secondary Role:**

---

## 🎯 Win-Win Challenges

*The core personal/professional challenges the client is here to overcome:*

1. 
2. 
3. 

---

## 📊 Personal Leadership Evaluation

| Area | Baseline | Current | Notes |
|---|---|---|---|
| Know my 5-year plan | | | |
| Professional Goal Clarity | | | |
| Plan on White Board | | | |
| Wheel of Life Development | | | |

---

## 🔄 Life Areas in Focus (EPL)

- [ ] Family & Home
- [ ] Financial & Career
- [ ] Mental & Educational
- [ ] Physical & Health
- [ ] Social & Cultural
- [ ] Spiritual & Ethical

**Primary Focus Areas:**

---

## 👨‍👩‍👧 Family / Genogram Notes

*Background context: family situation, key relationships, important dynamics*

---

## 📝 Important Facilitator Notes

### What NOT to do with this participant:

### How to care:

### People to network with this participant:

### Observed patterns:

### Important quotes or moments:

---

## 🎡 Wheel of Life

| Pillar | Score /10 | Priority | Actions / Goals to Improve |
|---|---|---|---|
| 3.1.1 Family & Home | | | |
| 3.1.2 Financial & Career | | | |
| 3.1.3 Mental & Educational | | | |
| 3.1.4 Physical & Health | | | |
| 3.1.5 Social & Cultural | | | |
| 3.1.6 Spiritual & Ethical | | | |

**6 Pillars of Personal Leadership Review:**

| Pillar | Score /10 | Goals to Improve |
|---|---|---|
| Personal Responsibility | | |
| Purpose | | |
| Plan | | |
| Passion | | |
| Positive Expectancy | | |
| Persistence | | |

---

## 🌟 Intangibles Registry

> *Behavioral or attitudinal habits identified together with the client. The client defines each scale level in their own words, self-scores at the start or end of each session, and sets a goal if improvement is desired.*

---

### Intangible #1: [Name Here]

**Definition:** *(What behavior/attitude are we tracking?)*

| Score | Description (client's own words) |
|---|---|
| **+10** | |
| **+5** | |
| **0** | |
| **-5** | |
| **-10** | |

**Scoring History:**

| Session | Date | Score | Goal Set? | Goal |
|---|---|---|---|---|
| | | | | |

---

### Intangible #2: [Name Here]

**Definition:**

| Score | Description (client's own words) |
|---|---|
| **+10** | |
| **+5** | |
| **0** | |
| **-5** | |
| **-10** | |

**Scoring History:**

| Session | Date | Score | Goal Set? | Goal |
|---|---|---|---|---|
| | | | | |

---

### Intangible #3: [Name Here]

**Definition:**

| Score | Description (client's own words) |
|---|---|
| **+10** | |
| **+5** | |
| **0** | |
| **-5** | |
| **-10** | |

**Scoring History:**

| Session | Date | Score | Goal Set? | Goal |
|---|---|---|---|---|
| | | | | |

---

## 📈 Tangible Indicators Tracking

> *Add/remove rows as needed. Types: number | ✓/✗ | yes/no*

| Indicator | Type | W01 | W02 | W03 | W04 | W05 | W06 | W07 | W08 | W09 | W10 | W11 | W12 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Program Lesson | # | | | | | | | | | | | | |
| PFS Score | /100 | | | | | | | | | | | | |
| Attendance | ✓/✗ | | | | | | | | | | | | |
| *(Add indicator)* | | | | | | | | | | | | | |
| *(Add indicator)* | | | | | | | | | | | | | |
| *(Add indicator)* | | | | | | | | | | | | | |

**Major Events (note the week):**

| Week | Event |
|---|---|
| | |

---

## 📚 Session Log

| # | Date | Lesson | PFS /100 | Key Outcomes | Note Link |
|---|---|---|---|---|---|
| 01 | | | | | |

---

## 🔗 Dream List Notes

*Key themes or dreams mentioned during sessions (not the full list — that lives in their Plan of Action):*

---

## 📖 Lesson Notes Summary

*A running summary of key insights per lesson — keep to 2-3 lines per session:*

| Lesson | Key Insight | Action Taken |
|---|---|---|
| L01 | | |
| L02 | | |

---

*Last updated: <% today %>*
