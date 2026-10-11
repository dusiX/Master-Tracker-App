# Master Tracker App — Portfolio Case Study

> **Portfolio/demo documentation.** This repository intentionally does not include the original `.msapp`, the source workbook, production flow exports, connection identifiers, or real recruitment records.

## Overview

Master Tracker App is a Microsoft Power Platform canvas app concept for bringing recruitment-related records and follow-up tasks into a single operational workspace. It uses a spreadsheet-backed data model and Power Automate flows for selected create, edit, and delete operations.

The project demonstrates low-code application design, Power Fx formulas, workflow integration, and structured operational data management.

## Business problem

Recruitment workflows often span several lists or spreadsheets: requisitions, interviews, internal offers, external offers, and follow-up actions. The app provides a unified interface to browse these records, filter tasks by status, and navigate to the relevant work area.

## Technology

- **Microsoft Power Apps (Canvas Apps)** — user interface, navigation, filtering, record selection, and form-based editing.
- **Power Fx** — formulas for filtering, sorting, navigation, validation, notifications, and invoking flows.
- **Microsoft Power Automate** — workflow actions called from the app and scheduled/email-driven automation in the wider solution.
- **Excel Online (Business)** — structured tables used as a lightweight data source.
- **JSON/YAML app source formats** — useful for reviewing control properties and formulas during development.

## App areas identified in the exported app source

- Main task dashboard
- Requisitions: L1–L11, LG, and FOBO
- Interviews
- Internal offers
- External offers
- Add/edit screens for requisitions, interviews, and offers

The exported app contains 13 screens and uses modern Power Apps controls including data grids, tab lists, text inputs, dropdowns, date pickers, and buttons.

## Main capabilities visible in the app source

- Navigate between task, requisition, interview, and offer views.
- Filter task lists by status.
- Select a task and launch the relevant workflow or editing screen.
- Copy a selected requisition/case identifier.
- Use form controls to add or edit requisition, interview, and offer records.
- Invoke Power Automate flows for selected data operations.
- Refresh displayed data after operations.

## Architecture (high level)

```text
Power Apps Canvas App
  ├── Main task dashboard
  ├── Requisition / interview / offer screens
  └── Power Fx formulas
          │
          ▼
Power Automate flows
  ├── Add / edit requisitions
  ├── Add / edit interviews
  ├── Add / edit offers
  └── Delete selected row
          │
          ▼
Excel Online (Business)
  └── Structured tables for tasks and recruitment records
```

This diagram describes the integration pattern. It does not contain production connection details.

## Engineering considerations

- **Data integrity:** identify rows using stable, unique keys and validate the key column before updating or deleting.
- **Error handling:** show success notifications only after the flow confirms success; surface actionable errors when a flow fails.
- **Excel connector limitations:** concurrent edits, table structure, row deletion, and delegation/performance limits should be tested with representative data.
- **Privacy:** use synthetic candidate names and fake identifiers in portfolio screenshots and examples.
- **Maintainability:** centralize repeated logic where practical and document flow inputs/outputs.

## Suggested next improvements

1. Add explicit success/failure responses to each Power Automate flow.
2. Standardize stable row keys across all tables.
3. Add confirmation before destructive actions.
4. Document the data dictionary and field mappings.
5. Add a test plan for empty values, duplicate IDs, invalid dates, and flow failures.
6. Replace production dependencies with a separate demo workbook and demo environment before sharing the app itself.

## Portfolio statement (draft)

Designed a Microsoft Power Platform-based recruitment tracking workspace using Power Apps, Power Automate, and Excel Online (Business). Built a multi-screen canvas app for navigating requisitions, interviews, offers, and task statuses; used Power Fx for filtering, validation, navigation, and flow invocation; and integrated workflow automation for record operations.

> Before using this statement, confirm which workflows are fully implemented and operational in the version you intend to present.
