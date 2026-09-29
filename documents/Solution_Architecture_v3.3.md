# NGT Group — Integrated System Architecture
**Working draft 5.3 (v3.3) · 28 September 2026 · supersedes Solution_Architecture_v3.2.md**

**v3.3 follows the CEO's answers** to the open questions of change request CR-2026-09 rev. 4 (28 September 2026). The architecture itself is unchanged. Updates:
- **Scheduled jobs:** SLA and SaaS acceptance reminders run against the cancel-by date, and the handover escalation goes to the Executives after 5 working days (Arch 18).
- **Outbox:** Admin names the approvers per email type (Arch 19).
- **Accounting system:** 1C; whether it can export status is being checked.
- **Prototype:** CR-2026-09 rev. 4 has been issued, with the open questions answered.
- **References:** now point to the current documents: CRM v3.3, Commercial v3.2, PM v3.3, Billing v3.6, Access v3.3 and Shared Data v3.1.

The v3.2 introduction follows.

**v3.2 records the prototype gap review of 27 September 2026** (NGT_CRM_Gap_Register). The review found that CR-2026-09 hasn't been started in the prototype yet (commit 89d1d2a). Changes:
- One architecture rule adopted from the prototype: the **approval-gated outbox** for every system-prepared email (Arch 19).
- One cross-module event: an **amendment during delivery** re-balances the open batches (Commercial 16, PM 23).
- The prototype's test count is updated, and leftover "scopes" now read "batches".

The module documents move to CRM v3.2, Commercial v3.1, PM v3.2, Billing v3.5 and Access v3.2. The v3.1 introduction follows.

**v3.1 reflects Billing_Module_v3.4 and the documents aligned with it** (CRM v3.1, PM v3.1, Access v3.1, Commercial v3, Shared Data v3; 26 September 2026). The billing "template engine" becomes one **recurring engine**:
- three settings per contract (accrual, billing, anniversary);
- presets per product;
- four joining rules;
- billed and accrued amounts kept as separate records.

Project billing runs on **delivery batches** and **advances**. Two new scheduled jobs are needed: renewal acceptance and annual quotes, and renewal-tender alerts.

v3 recorded the architecture decisions from the review of Luka Geldiashvili's CRM prototype (25 September 2026). The design now requires a **PostgreSQL** database, a **fresh TypeScript production build**, and the prototype as the **test bench and UI reference**. It also narrows the first release: supplier costs, invoice tracking and fully open billing formulas are deferred. It remains a high-level design, not a build specification.

## Changes from v3.2 (v3.3)

| Area | v3.2 | v3.3 | Source |
|---|---|---|---|
| Scheduled jobs | Acceptance windows for Care; handover reminders and escalation | Adds SLA and SaaS acceptance reminders 60 and 30 days before the cancel-by date; escalation to the Executives after 5 working days | Arch 18; Billing 63–64 |
| Outbox | Recipients or designated approvers | Admin names the approvers per email type | Arch 19; Billing 65 |
| Accounting integration | Open | Accounting system is 1C; status export being checked | §7; Billing 66 |
| Prototype | CR-2026-09 rev. 3, not started | Rev. 4 issued with the open questions answered; implementation next | §7 |
| References | Several pointed to v3.1 or v3.4 documents | Current documents | §1, §4–7 |

## Changes from v3.1 (v3.2)

| Area | v3.1 | v3.2 | Source |
|---|---|---|---|
| Email | The system never sends email | Every system-prepared email goes through one approval-gated outbox | Arch 19 |
| Cross-module events | Official delivery, anniversary, prepaid term end | Adds: amendment confirmed → PM re-balances open batches, Billing previews | §3; Commercial 16; PM 23 |
| Prototype | 527 checks | 563 checks at commit 89d1d2a; CR-2026-09 not started | Arch 13; §7 |
| Rollout wording | "PM with scopes" | "PM with batches" | §6 |

## Changes from v3 (v3.1)

| Area | v3 | v3.1 | Source |
|---|---|---|---|
| Billing engine | Template per recurring type, with overrides | **One recurring engine**: contract settings, presets, four joining rules, overrides; billed items and accrual items stored separately | Decision 7; Arch 17; Billing 24, 32, 52 |
| Project billing | Delivery scope confirms charges | **Delivery batch** with one-off and recurring allocations; **advance** of 0–100% offset against batch invoices | Arch 17; Billing 45–51, 59 |
| Scheduled work | Reminders, renewal states, Cold, sync, imports | Adds contract-year generation, acceptance windows, annual-quote preparation, supplementary charges, renewal-tender alerts and opportunities, renewal-revenue forecasts | Arch 18 |
| Cross-module events | Won → project | Adds signing date → advance; official delivery → batch invoice and recurring joins; prepaid term end → Renewal tender in CRM | §3 |

## Changes from v2

| Area | v2 | v3 | Source |
|---|---|---|---|
| Database | One relational database (recommended) | **PostgreSQL required**, with row-level security and server-side reporting | Arch 11 |
| Build approach | Stack undecided | **Fresh build in TypeScript**, modular. The prototype is not the production codebase. | Arch 12 |
| Role of the prototype | Not known | **Test bench** for staff walkthroughs and the UI reference; its tests merge into the acceptance catalogue | Arch 13 |
| Firebase | Not considered | **Considered and rejected** for production | Arch 11 |
| Code ownership | — | Repository in an **NGT-owned GitHub organisation**, with CI on every push | Arch 14 |
| Scheduled work | Background worker | Background worker is **mandatory**; nothing depends on a user opening the app | Arch 15 |
| Billing engine | General formula/workflow runtime | **Template engine** per recurring type, with overrides and manual schedules | Decision 7 revised; Billing 11 |
| PM depth | Dependencies, rescheduling, effort, workload | Tasks, milestones, scopes; the rest deferred | Decision 4 revised; PM 13 |
| Supplier costs | Part of the first operating release (foundations) | **Deferred to a later release** | Decision 8 revised |
| monday.com | Replace relevant workflows | **Confirmed: replace**, then read-only. Never a source of truth for the new system. | Arch 16 |
| Directions | Digital signage, VOIX | Digital Signage, VOIX + CF | CRM 62 |

## 1. Decision record

| Ref | Decision | Status |
|---|---|---|
| 1 | First-release outcomes: sales visibility and delivery coordination | Confirmed |
| 2 | NGT at launch; structured for sister companies later | Confirmed |
| 3 | ERP boundary: supplier cost tracking only; no purchasing or inventory | Confirmed; Costs itself deferred (decision 8) |
| 4 | PM depth | **Revised:** tasks, milestones and delivery batches in the first release; dependencies, rescheduling, effort and workload later (PM 13, PM 20) |
| 5 | Every won opportunity creates its own project | Confirmed |
| 6 | Billing calculates charges and reminders; invoicing is external | Confirmed |
| 7 | Billing flexibility | **Revised again (v3.1):** one recurring engine. Each contract has three settings (accrual, billing, anniversary); presets per product; four joining rules (after year 1, units from delivery, aligned to anniversary, prepaid term); overrides and manual schedules with reasons. General formula authoring is deferred (Billing 11, 24, 32, 52). |
| 8 | Post-Won supplier costs and margin after supplier costs; no labour costs | **Deferred** to a later release; the design (Costs_Module_v2.md) is kept |
| 9 | Replace HubSpot and the relevant monday.com workflows | Confirmed (Arch 16) |
| 10 | Access by role, direction and assignment; explicit sharing; combined roles | Confirmed; launch roles and actions in Access v3.3 (a cross-direction share shows the record, not its values) |
| Arch 11 | **PostgreSQL** is the database. Row-level security enforces direction and assignment scope; field and aggregate checks run on the server. Reporting runs server-side in SQL. Firebase/Firestore was considered and rejected: its document rules cannot hide fields within a record or protect aggregates, and the reporting is relational. | Confirmed |
| Arch 12 | Production is a **fresh build**: TypeScript front end and back end, a modular monolith, typed data access, database migrations and automated tests. It suits an in-house team working with AI-assisted development. | Confirmed |
| Arch 13 | The **prototype is the test bench**. It is aligned to the v3 rules through change request CR-2026-09 and used for walkthroughs with salespeople, PMs and accountants before build. Its screens are the UI reference, and its checks (563 at commit 89d1d2a) merge with the review scenarios of the module documents into one **acceptance-test catalogue**. It never holds real customer data. | Confirmed |
| Arch 14 | All code for the system lives in an **NGT-owned GitHub organisation**, with CI running the tests on every push. | Confirmed |
| Arch 15 | All scheduled work (reminders, renewal states, Cold suggestions, return dates, calendar sync, imports) runs in a **background worker** on a schedule, and is retry-safe. | Confirmed |
| Arch 16 | monday.com is a **migration source only**. Each module's relevant boards become read-only at cutover. | Confirmed |
| Arch 17 | **Billing data model.**<br>• Recurring contracts: customer, direction, product line, settings, anniversary, auto-renew.<br>• Recurring lines: revenue type, joining rule, amount basis.<br>• Contract years: total, acceptance, quote.<br>• **Billed items and accrual items as separate records**, each storing the calculation, rule version or override behind it.<br>• Delivery batches with allocations; advances with offsets; prepaid terms with coverage end and expected renewal value.<br>Every calculation uses decimals and whole months, and the last month takes the rounding. | Confirmed (Billing v3.4) |
| Arch 18 | **Billing scheduled jobs**, in the background worker and retry-safe:<br>• contract-year generation at each anniversary;<br>• acceptance windows (4–3 months ahead for Care) and overdue states; SLA and SaaS acceptance reminders 60 and 30 days before the cancel-by date (Billing 63);<br>• annual-quote preparation (1 month ahead);<br>• supplementary charges for late deliveries;<br>• Renewal tender alerts and CRM opportunities 6 months before a prepaid term ends;<br>• expected renewal revenue forecasts;<br>• handover reminders, and escalation to the Executives after 5 working days, configurable (Billing 64).<br>A job that runs twice never duplicates items, alerts or opportunities. | Confirmed (Billing v3.4; v3.6) |
| Arch 19 | **Approval-gated outbox.** Any email the system prepares (billing changes, annual quotes, later reminders) is queued, never sent. A recipient or designated approver (named per email type by an Admin, Billing 65) reviews and may edit it, opens it in their own mail app, sends it, and marks it sent or discards it. Preparation and the final step are audited. This replaces any plan to send through the Gmail API. *Adopted from the prototype.* | Confirmed (gap review, 27 Sep 2026) |

**Out of scope for the first release:**
- Supplier costs and margin (Costs module later).
- Invoice sent/paid tracking and receivables; a read-only paid flag from accounting may come later.
- Account health score.
- Product catalogues, quotes and in-app proposal generation.
- A user-editable automation engine, custom fields and a report builder.
- Service tickets. Where support lives (this app or Jira Service Management) is to be decided.
- Web lead forms and the lead inbox.
- The international VOIX partner model.
- Purchasing, inventory, accounting, payroll and labour costing (permanent boundaries).

**Open:** hosting provider, data residency and authentication provider. Google Workspace sign-in restricted to @ngt.ge is the working assumption. The launch user count is about ten.

## 2. Overall design

One **modular monolith** with a shared foundation and one PostgreSQL database. Modules own their tables and write only through their own operations.

| Module | Owns (first release) | Connects to |
|---|---|---|
| Shared foundation | Organizations, contacts, parent accounts, users, role grants, directions, lists, GEL rates, documents, activity links, audit, notifications, Morning Brief | Every module |
| CRM | Opportunities (Lead to Won/Lost), shared pipeline and options, one-off amounts, recurring lines, related deals, activities, tasks, targets, email templates | Commercial, PM, Google Workspace, Billing (Upsell) |
| Commercial | Proposal revisions, purchases, agreements, revenue lines, amendments, approvals | CRM, PM, Billing |
| Project management | Projects (including projects with no sale value), templates, tasks, milestones, delivery batches and their allocations, handover, cancellation review | Commercial, Billing |
| Billing | Recurring contracts and settings, presets and joining rules, contract years, billed items, accrual items, renewal acceptance, annual quotes, advances and offsets, prepaid terms and renewal forecasts, overrides, handovers, adjustments | Commercial, PM (batches), CRM (Upsell leads, Renewal tenders) |
| Reporting | Permission-filtered dashboards and GEL consolidation | All modules |
| *Supplier costs (later)* | Suppliers, estimates, actuals, allocations, margin | Projects, management reporting |

## 3. The commercial chain

The basic chain is unchanged from v2:
- customer → opportunities → proposal revisions → accepted purchase or agreement → amendments;
- one project per won opportunity;
- CRM recurring line → Commercial line (with its joining-rule terms) → Billing recurring contract;
- renewals stay in Billing.

v3.1 adds these events:

| Event | Effect |
|---|---|
| Won with **signing date** (CRM 81) | Billing records the advance (0–100%); the advance invoice is issued outside the system |
| Project split into **delivery batches** (PM 20) | Each batch carries its one-off share and recurring allocations |
| Accountant enters the **official delivery date** (Revenue Service sign-off) | Batch invoice: one-off share + year-1 recurring − advance offset. Its recurring items join the customer's contracts by their joining rules. Supplementary charges are created where they apply. |
| Anniversary | New contract year: total, accruals and billed items, according to the settings |
| 6 months before a **prepaid term** ends | Alert, and a **Renewal tender** opportunity in CRM; expected renewal revenue from the end date |
| Project with **no sale value** officially delivered | SLA units change |
| **Amendment** confirmed after Won, including during delivery (Commercial 16) | Contract totals change; PM re-balances the batches not yet officially delivered (PM 23); Billing previews the effect. The CRM deal keeps the sold values (CRM 85). |

## 4. Module summaries

- **CRM** (CRM_Module_v3.3.md):
  - Lead as the first stage of one shared pipeline, with optional Tender and PoC stages.
  - Next action required; "stale" means overdue or missing.
  - Probability override; Nurture, Postponed and Cold.
  - One-off amount plus recurring lines; targets; the Morning Brief; no costs.
  - **Signing date required for Won; Renewal tender opportunities.**
  - Won locks the sold amounts; deal summary and flags; sales analysis (v3.2).
  - Manual Renewal tenders, contact-coverage threshold, "Emails to approve" in the brief, briefs viewable by direction managers and Executives (v3.3).
- **Commercial** (Commercial_Module_v3.2.md):
  - External proposals, revisions, discount and payment-term approvals, amendments.
  - **Advance terms, recurring terms per joining rule, one-off breakdown (HW / SW / PS).**
  - Changes after Won, including during delivery, are amendments (v3.1), recorded by the Owner, the direction manager or the project's PM (v3.2).
- **PM** (PM_Module_v3.3.md):
  - Template checklists per direction × delivery type.
  - **Delivery batches with allocations**, with a send-to-accountant handover.
  - **Projects with no sale value**; cancellation review.
  - Re-balancing open batches after an amendment; handover notifications (v3.2); the PM records amendments; seed templates for all directions (v3.3).
- **Billing** (Billing_Module_v3.6.md):
  - Vocabulary (accrued, billed, paid) and the recurring engine with presets and four joining rules.
  - Care (Types 1 and 2), SLA and SaaS for CEM/Qmatic, and the D-ID products.
  - Batches and advances; renewal acceptance and annual quotes; renewal tenders; Billing changes view; Done and adjustments.
  - Handover document, contract notice period and cancel-by date, outbox (v3.5).
  - SLA and SaaS acceptance by the cancel-by date; escalation to the Executives; outbox approvers named by Admin (v3.6).
- **Access** (Access_and_Permissions_v3.3.md): six launch roles, default deny, the billing and PM actions, activity edits and the audit viewer; viewing other people's briefs; record-only sharing.

## 5. Technical structure

| Layer | Choice |
|---|---|
| Database | PostgreSQL, with row-level security policies per direction and assignment |
| Back end | TypeScript API; module services; server-side authorization for fields and aggregates |
| Front end | TypeScript single-page web client; responsive; English and Georgian |
| Worker | Background job runner for schedules, reminders, sync and imports; idempotent jobs |
| Money | Decimal types in the database; integer minor units or a decimal library in code; explicit rounding (the last month of a contract year takes the difference) |
| Calculation engine | Pure, tested functions per joining rule and setting. Inputs and results are stored on each billed and accrual item. Changes run as previews before they are applied. The worked examples in Billing v3.6 §5 (unchanged since v3.4) are acceptance tests. |
| Dates | ISO 8601 with time zones; date-only fields for billing periods |
| Documents | Object storage with record-level access |
| Integrations | Google Workspace (Calendar read, Gmail add-on), monday.com and HubSpot import; Jira later |
| Quality | Typed code, migrations under version control, the acceptance-test catalogue in CI, backups and restore tests |

The specific framework, hosting provider and region are chosen when hosting and data residency are decided.

## 6. Rollout

A proposed sequence, not an agreed timetable:

| Stage | Deliverable | Exit evidence |
|---|---|---|
| 0. Validate | Prototype aligned through CR-2026-09; 3–4 walkthrough sessions with salespeople, a PM and an accountant | Walkthrough findings folded into the v3 documents |
| 1. Foundation | Shared records, role grants, lists, GEL rates, import tooling, CI | Scope boundaries pass the access scenarios |
| 2. First operating release | CRM with the Morning Brief and Google Calendar/Gmail logging; Commercial capture; PM with batches and handover | A real opportunity flows from Lead to confirmed delivery |
| 3. Billing | Recurring engine and presets, batches and advances, accrual schedules, acceptance and quotes, renewal tenders, Billing changes, handover | The Billing v3.6 worked examples pass, and real agreements per preset reproduce current billing and accruals |
| Later | Costs; the lead inbox and web forms; dependencies and workload; Jira; service tickets; accounting page; read-only paid flag; mobile; AI | Each has a defined benefit and owner |

**Migration** follows Shared_Data_and_Migration_v3.1.md. The CRM stage mapping is re-pointed to the shared pipeline. Billing imports each contract's settings and joining-rule inputs, the current contract year, and open projects' batches and advances (Data 11–14). Keep the existing billing process running until Billing reconciles.

## 7. Status

| Area | Status | Next |
|---|---|---|
| CRM | v3.3 | Update the monday.com stage mapping; the Renewal tender's first next action |
| Commercial | v3.2 | Approval limits; default advance per segment |
| PM | v3.3 | Default PMs and direction-specific task lists; design of the batch-splitting and re-balancing screen |
| Billing | v3.6 | CEM/Qmatic and D-ID done; the other directions expected to reuse the same rules; Type 3 public Care parked |
| Access | v3.3 | Production user-to-role mapping (the test-bench mapping is in CR-2026-09 rev. 4) |
| Costs | v2, deferred | Revisit after the first operating release |
| Data / migration | v3.1 | Stage mapping update; Monday recurring-payment and Projects boards; official delivery dates and advance offsets from accounting |
| Prototype | CR-2026-09 rev. 4 issued 28 Sep 2026, open questions answered; not started at commit 89d1d2a | Implement the CR wave by wave, then the walkthroughs |

**Key unresolved choices:**
- Hosting, data residency and authentication.
- Approval thresholds.
- Default PMs and direction-specific task lists (the seed lists apply to all directions, PM 25).
- Where support tickets live.
- Whether 1C, the accounting system, can export invoice and payment status.
- The accounting treatment of prepaid periods accrued at delivery.
- What the auto-renew clause changes for CEM Care.
- Who owns the shared monthly GEL rate table (several direction managers maintain it today).

**Sources:** Solution_Architecture_v2.md and v3; all current module documents (CRM v3.3, Commercial v3.2, PM v3.3, Billing v3.6, Access v3.3, Shared Data v3.1); the NGT CRM prototype's ARCHITECTURE.md and PROCESSES.md; change request CR-2026-09; decisions confirmed by the CEO on 25–26 September 2026; the prototype gap review (NGT_CRM_Gap_Register, 27 September 2026); the CEO's answers to the open questions of change request CR-2026-09 rev. 4 (28 September 2026).
