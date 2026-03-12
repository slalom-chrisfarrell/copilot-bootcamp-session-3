# Product Requirements Document (PRD) - TODO App Upgrade (MVP + Post-MVP Roadmap)

## 1. Overview

The TODO app is currently a basic task tracker with title and completion status. This upgrade introduces lightweight planning features so users can better organize and act on tasks without adding technical complexity.

The product goal is to deliver a simple, teachable MVP that remains frontend/local-storage based (no backend changes), while clearly separating additional usability enhancements into Post-MVP.

---

## 2. MVP Scope

- Add optional `dueDate` to each task.
- `dueDate` must use ISO format `YYYY-MM-DD` when provided.
- Invalid `dueDate` values are ignored and treated as if no due date is set.
- Add `priority` field to each task with enum values: `P1`, `P2`, `P3`.
- Default `priority` to `P3` when not specified.
- Keep `title` as a required field.
- Add filters to the task list:
  - All
  - Today
  - Overdue
- Keep data persistence local only (local storage), with no backend or external storage integration.
- Make no backend/API changes as part of MVP.

---

## 3. Post-MVP Scope

- Visually highlight overdue tasks to make them stand out.
- Add sorting behavior with this precedence:
  - Overdue tasks first
  - Then by priority (`P1` before `P2` before `P3`)
  - Then by due date ascending
  - Tasks without due dates last

---

## 4. Out of Scope

- Notifications/reminders
- Recurring tasks
- Multi-user or collaboration features
- Keyboard navigation improvements
- Special accessibility enhancements beyond existing baseline
- Any external storage or backend persistence changes
