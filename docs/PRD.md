# Product Requirements Document (PRD) – LifeStint
**Tagline:** *Small sprints. Big results.*

## 1. Purpose
LifeStint is a lightweight productivity app that helps users track focused work sessions (“stints”) across multiple projects, providing simple analytics and quality-of-life features.

---

## 2. Key Features

### Dashboard
- Displays all active projects as cards.
- Each card shows:
  - Project name.
  - Daily stint progress badge (e.g., **1 of 3 stints today**, based on expected daily stints per project).
  - Action buttons for Start, Pause/Resume, and Stop.
- Toggle to **show/hide inactive projects**.
- **Clearly highlight the active stint** with a visible timer and distinct styling.
- **Only one stint can be active at a time** — starting a stint automatically ends any currently active stint.
- Buttons to **create** and **edit** projects in modal dialogs.

### Stints
- **Default stint duration configurable per user** (global default: 2 hours).
- Per-project override for stint duration.
- Pause/Resume functionality.
- Maximum stint duration limit (auto-stop if exceeded).
- End reason tracking (manual stop vs. timeout).
- **Notes/comments field** at the end of each stint with **Markdown formatting support**.

### Project Management
- Create, edit, and archive projects.
- Activate/deactivate projects without deletion.
- Set **expected number of stints per day** per project.

### Notifications
- Alert when a stint is about to end.

### Reporting
- **Per project:** total stints, average per day, progress toward daily expected stints.
- **Overall:** total stints across all projects, weekly and monthly summaries.

---

## 3. Flow

1. **Project Setup**
   - User creates a project (via modal), sets an expected number of daily stints, and optionally customizes stint duration.

2. **Stint Start**
   - From the dashboard, the user clicks **Start** on a project card.
   - Timer begins, based on the configured stint duration.
   - Any other active stint is automatically stopped.

3. **During Stint**
   - User can **Pause/Resume** as needed.
   - Dashboard clearly marks the active stint card.
   - System tracks elapsed time in real-time.

4. **Stint End**
   - Can end manually or auto-stop when the maximum duration is reached.
   - System records end reason.
   - User is prompted to **add notes/comments** (Markdown supported).

5. **Notifications**
   - A configurable alert triggers shortly before the stint ends.

6. **Reporting**
   - Dashboard updates project’s daily progress (e.g., “2 of 3 stints today”).
   - Data stored in Supabase for historical reporting (per project and overall).

---

## 4. Non-Functional Requirements
- **Performance:** Instant UI updates without page reload.
- **Scalability:** Handle up to hundreds of projects and thousands of stints without slowdowns.
- **Cross-Platform:** Works on desktop and mobile browsers.
- **Persistence:** All data stored in Supabase backend.

---

## 5. Tech Stack
- **Frontend:** Next.js (React)
- **Backend:** Supabase
- **Auth:** Supabase Auth
- **Styling:** Tailwind CSS
- **Notifications:** Browser Notifications API
- **Markdown Rendering:** e.g., `react-markdown`

---

## 6. Success Metrics
- User can create a project, set expected daily stints, and log their first stint within 1 minute of onboarding.
- Daily stint tracking accuracy ≥ 99%.
- Notifications delivered within 2 seconds of trigger.

---

## 7. Dashboard Wireframe (Text Representation)

```
-----------------------------------------------------------
| LIFE STINT                                [+ Add Project]|
| Tagline: Small sprints. Big results.                     |
-----------------------------------------------------------
| [ACTIVE] Project Alpha  (1 of 3 stints today) [Edit]     |
| Timer: 01:12:45                                          |
| [Pause] [Stop]                                           |
-----------------------------------------------------------
| Project Beta  (0 of 2 stints today) [Edit]               |
| [Start]                                                  |
-----------------------------------------------------------
| Project Gamma  (2 of 4 stints today) [Edit]              |
| [Start]                                                  |
-----------------------------------------------------------
Legend:
- [ACTIVE] card is visually highlighted (e.g., glowing border, bold timer).
- Only one project can show [ACTIVE] at a time.
- Toggle hides/shows inactive projects.
- Add Project and Edit Project open modal forms.
```
