# Vault Setup & Obsidian Configuration Guide

> **📋 Quick Navigation**
> [[#Step 1: Open This Vault in Obsidian]] · [[#Step 2: Recommended Plugins (all free, install via Settings → Community Plugins)]] · [[#Step 3: Configure Templater]] · [[#Step 4: Set Up QuickAdd for New Session (Optional but Powerful)]] · [[#Step 5: Adding a New Client]] · [[#Step 6: Starting a New Session]] · [[#Step 7: WhatsApp Link (Future)]] · [[#Step 8: AI Transcript Action Steps (Current Workflow)]] · [[#Dataview Example Queries]]

---

## Step 1: Open This Vault in Obsidian

1. Open Obsidian → **Open folder as vault**
2. Navigate to and select the `Keystone-Obsidian-Vault` folder
3. Trust the vault when prompted

---

## Step 2: Recommended Plugins (all free, install via Settings → Community Plugins)

| Plugin | Install Name | Why |
|---|---|---|
| **Dataview** | `dataview` | Query sessions, scores, client lists across the vault |
| **Templater** | `templater-obsidian` | Auto-fill {{date}}, {{CLIENT_NAME}}, session numbers |
| **Calendar** | `calendar` | Visual session date navigation |
| **QuickAdd** | `quickadd` | One-command new session note creation |

---

## Step 3: Configure Templater

In Settings → Templater:
- Set **Template folder** to `00-Templates`
- Enable **Trigger Templater on new file creation**
- Add a hotkey for **Open Insert Template modal** (e.g., Alt+T)

---

## Step 4: Set Up QuickAdd for New Session (Optional but Powerful)

1. Install QuickAdd
2. Add a **Template choice** called "New Session Note"
3. Point it to `00-Templates/Session-Note.md`
4. Set output path to `01-Clients/{{VALUE:Client Name}}/Sessions/`
5. Set filename format to `{{DATE:YYYY-MM-DD}}-Session-{{VALUE:Session #}}-L{{VALUE:Lesson}}`

Now you can open a new session note in 3 keystrokes.

---

## Step 5: Adding a New Client

1. Create folder: `01-Clients/[FirstName-LastName]/`
2. Create subfolder: `01-Clients/[FirstName-LastName]/Sessions/`
3. Duplicate `00-Templates/OPFMS-Client-Master.md` into the client folder
4. Rename it: `OPFMS-[FirstName-LastName].md`
5. Fill in the YAML frontmatter and Participant Profile section

---

## Step 6: Starting a New Session

1. Open the client's `OPFMS-[Name].md` → scroll to **Session Log** for carry-forward items
2. Duplicate `00-Templates/Session-Note.md` into `01-Clients/[Name]/Sessions/`
3. Rename: `YYYY-MM-DD-Session-XX-LXX.md`
4. Fill **Carry-Forward** from the previous session note
5. Run the session and fill notes in real time
6. At end of session: fill **Goals**, **PFS Scoring**, **Assignment Selector**
7. Copy the **Client Summary Draft** into `00-Templates/Client-Summary-Email.md` → finalize → send

---

## Step 7: WhatsApp Link (Future)

When you're ready to share session summaries via WhatsApp link:
- Use **Obsidian Publish** (paid) to publish specific notes
- Or use a **self-hosted sync** (Syncthing + a simple markdown web server)
- Or export the note as PDF and share via WhatsApp

*We'll set this up when you're ready — it requires one additional tool decision.*

---

## Step 8: AI Transcript Action Steps (Current Workflow)

1. After your Zoom/Fathom session ends, download or copy the transcript
2. Open the session note → **AI-Derived Action Steps** section
3. Paste the transcript excerpt into the code block
4. Ask your AI assistant: *"From the transcript below, extract ONLY concrete action steps or commitments the client or coach recommended. List as bullets."*
5. Paste the extracted action steps into the field below

*Future automation: When Fathom/Zoom offers a webhook, we can auto-populate this field.*

---

## Dataview Example Queries

Add these as code blocks in any note using ` ```dataview ` :

### List all active clients:
```dataview
TABLE status, program, total_sessions
FROM "01-Clients"
WHERE file.name = "OPFMS-" + client_name
SORT client_name ASC
```

### All sessions in the last 30 days:
```dataview
TABLE client_name, lesson_covered, pfs_score, session_type
FROM "01-Clients"
WHERE contains(tags, "session")
SORT session_date DESC
LIMIT 20
```

### Clients with sessions this week:
```dataview
TABLE client_name, session_date, lesson_covered
FROM "01-Clients"
WHERE contains(tags, "session") AND session_date >= date(today) - dur(7d)
SORT session_date ASC
```

---

*The Keystone Group · Leadership & Legacy Development*
