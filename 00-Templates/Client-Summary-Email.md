<%*
const clientName = await tp.system.prompt("Client Full Name");
const sessionNum = await tp.system.prompt("Session Number (e.g., 01)", "01");
const lessonNum = await tp.system.prompt("Lesson (e.g., L02)", "");
const sentVia = await tp.system.suggester(
  ["📧 Email", "💬 WhatsApp"],
  ["Email", "WhatsApp"]
);
const today = tp.date.now("YYYY-MM-DD");
const todayLong = tp.date.now("MMMM DD, YYYY");
const slug = clientName.replace(/ /g, "-");
await tp.file.rename(`Summary-${slug}-Session-${sessionNum}`);
-%>
---
client_name: "<% clientName %>"
session_date: "<% today %>"
session_number: <% sessionNum %>
lesson: "<% lessonNum %>"
status: "Draft"
sent_via: "<% sentVia %>"
tags: [summary, <% slug %>]
---

# Client Summary — <% clientName %> — Session <% sessionNum %>

> **Date:** <% todayLong %> | **Send via:** <% sentVia %> | **Status:** Draft
> *Finalize everything below, then copy and send.*

---

Hello <% clientName %>,

It was great connecting with you today. Here is a summary of what we agreed on, along with your goals and assignment for the coming week.

---

## ✅ Your Goals for This Week

### Personal Goals:
- 
- 

### Professional Goals:
- 
- 

### Intangible Goal — [Name]:
- 

---

## 📚 Assignment for Next Session

Please read and listen to **Lesson ___: [Title]** for a combined total of **6 repetitions**.

Complete the following forms (attached / available on the platform):

| # | Form | Instructions |
|---|---|---|
| 1 | M020 — Participant Feedback (PFS) | Fill all fields after completing the lesson |
| 2 | M021 — Action Steps Log | Log each date you listen, read, or work on action steps |
| 3 | | |

**Lesson audio link:** [Box Link]

**Additional reading / article:** *(if applicable)*

---

## 💬 A Note from Your Coach

*(Personal, encouraging closing — 2–3 sentences)*

---

Looking forward to our next session.

Positively,

[Your Name]
The Keystone Group · Leadership & Legacy Development

---

*"If you are not making the progress you would like to make and are capable of making, it is merely because your goals are not clearly defined." — Paul J. Meyer*
