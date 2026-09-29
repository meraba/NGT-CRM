# NGT Group — Project Context and Aims

**Reusable companion for module-level design · Version 3.3 · 28 September 2026 · supersedes NGT_Project_Context_and_Aims_v3.2.md**

## Changes from v3.2

The CEO answered the 17 open questions raised while preparing change request CR-2026-09 rev. 4 (28 September 2026). The module documents record the 13 that affect the design; Q3, Q4, Q6 and Q7 concern the prototype only (CR-2026-09 §10):

| Area | v3.2 | v3.3 |
|---|---|---|
| CRM | v3.2 | v3.3: seeded pipeline accepted; contact-coverage threshold 1,000,000 GEL per direction; manual Renewal tenders; "Emails to approve" in the brief; briefs viewable by direction managers and Executives; a derived overall company status |
| Commercial | v3.1 | v3.2: amendments recorded by the deal Owner, the direction manager or the project's PM |
| PM | v3.2 | v3.3: the PM records amendments; the seed task lists apply to all six directions, with no default PMs yet |
| Billing | v3.5 | v3.6: SLA and SaaS acceptance due by the cancel-by date; escalation to the Executives after 5 working days; outbox approvers named by Admin; 1C named as the accounting system |
| Access | v3.2 | v3.3: Access 24 adopted, Access 25 decided (PMs included); a cross-direction share shows the record, not its values |
| Architecture | v3.2 | v3.3: scheduled jobs and outbox updated; references to the current documents |
| Prototype | CR-2026-09 rev. 3 | Rev. 4 issued, covering the gap review and these answers |
| UI | UI_Reference_Luka_Prototype | NGT_UI_Style_Guide v1: the visual style and the UI decisions kept from Luka's prototype, for new prototypes |

## Changes from v3.1

The prototype gap review of 27 September 2026 (NGT_CRM_Gap_Register) compared Luka's prototype, at commit 89d1d2a, with the v3 documents. CR-2026-09 has not been started in the prototype yet. Of the 29 prototype rules the v3 documents didn't cover, the CEO confirmed 18 for adoption.

| Area | v3.1 | v3.2 |
|---|---|---|
| CRM | v3.1 | v3.2: Won locks the sold amounts; deal summary and two more flags; task reminders, personal tasks, the brief's "seen" marker and a suggested first next action; sales analysis; editing own activities; scoped search; customer status per direction |
| Commercial | v3 | v3.1: every change after Won, including during delivery, is an amendment; one-off breakdown HW / SW / PS |
| PM | v3.1 | v3.2: re-balancing open batches after an amendment; handover notifications |
| Billing | v3.4 | v3.5: handover document at official delivery; contract number, notice period and cancel-by date; the outbox for system-prepared emails |
| Access | v3.1 | v3.2: activity edits, audit viewer, scoped search; proposed rules for viewing others' briefs and recording amendments |
| Architecture | v3.1 | v3.2: approval-gated outbox (Arch 19); amendment event |
| Shared data | v3 | v3.1: contract number, term and notice period in the billing import |

## Changes from v3

| Area | v3 | v3.1 |
|---|---|---|
| Billing | Templates per recurring type, overridable | **One recurring engine**: accrued/billed/paid vocabulary; three settings per contract (accrual, billing, anniversary); presets; four joining rules; delivery batches; advances of 0–100%; renewal acceptance and annual quotes; renewal tenders (Billing v3.4) |
| CRM | — | **Signing date required for Won**; **Renewal tender** opportunity type (CRM v3.1) |
| PM | Delivery scopes | **Delivery batches** carrying one-off and recurring allocations; **projects with no sale value** (PM v3.1) |
| Commercial | v2 | v3: advance terms, recurring terms per joining rule, one-off breakdown |
| Access | v3 | v3.1: the new billing and PM actions |
| Migration | v2 | v3: billing inputs, current contract year, open batches and advances |
| Content | v3 condensed v2 and dropped still-valid rules | **Restored**: vision detail, the "reduce fragmented records" aim, module connections, lifecycle concepts, access rules, architecture principles, transition rules, and the method and opening prompt for new conversations |
| Product catalogue | v3 listed it under "not in the first release" (an error) | **Permanently out of scope** (Commercial 7), as in v2 |

## 1. Purpose of this document

Use this brief together with the description of whichever module is being refined. It gives a new conversation the business context, intended product, shared rules and connections that must stay consistent as modules become more detailed.

It describes the complete intended product within the agreed boundaries. Release order is noted where it has been decided. The project is in functional design: module documents contain confirmed decisions, recommendations and open details; they do not describe implemented software. The rules below are confirmed unless marked as proposed or open.

**Current document set (28 September 2026):**

| Document | Version | Status |
|---|---|---|
| NGT_Project_Context_and_Aims | v3.3 | This brief |
| Solution_Architecture | v3.3 | Current |
| CRM_Module | v3.3 | Current |
| Commercial_Module | v3.2 | Current |
| PM_Module | v3.3 | Current |
| Billing_Module | v3.6 | Current; CEM/Qmatic and D-ID rules; other directions expected to reuse them |
| Access_and_Permissions | v3.3 | Current |
| Shared_Data_and_Migration | v3.1 | Current |
| Monday_Migration_Mapping | v1 | Current; stage table to update for the shared pipeline |
| Costs_Module | v2 | **Deferred** to a later release; kept for reference |
| CHANGE_REQUEST CR-2026-09 (rev. 4) and CHANGELOG | — | Instructions for aligning Luka's prototype, the test bench; not yet started at commit 89d1d2a |
| NGT_CRM_Gap_Register | 27 Sep 2026 | The prototype checked against the v3 documents in both directions (published page and Excel file) |
| NGT_UI_Style_Guide | v1 | Visual style, layout and UI decisions kept from Luka's prototype, with tokens and reference screenshots; for any new prototype |

Where an older version conflicts with a current one, the current one wins. Earlier versions are kept for reference only.

## 2. Vision and business context

NGT Group wants one integrated internal application connecting **CRM, commercial management, project delivery and billing management**, with supplier-cost tracking to follow in a later release. The record should show what is being pursued, what was sold, what must be delivered and what the customer should be charged and when. Information should flow through the customer lifecycle without re-entry or loss of context.

NGT is a technology integrator, product vendor and service provider. Its **six business directions** are:
- CX / Queue management (Qmatic), also called CEM.
- Digital ID / Security (D-ID).
- Cash handling.
- Digital Signage.
- VOIX + CF (Customer Feedback).
- Kiosks.

They differ in sales cycles, delivery patterns and recurring-service arrangements.

Customers buy hardware, licences, professional services and custom development. They then continue with recurring services of three revenue types: **Care/Maintenance, SaaS and SLA**. Later purchases add branches, users, licences, functionality or hardware, so one customer relationship spans many opportunities, projects and agreements. Some products are NGT's own (VOIX, Mobile Token); many are resold (Qmatic, HSMs, Ezio).

Direct and partner sales are both supported. For partner deals, the invoiced partner is the account and there is no end-customer field. The detailed international VOIX partner model is deferred.

Scope is NGT Group, structured so sister companies can be added. A direction is an organizational boundary, not a separate customer database.

## 3. What the project should achieve

| Aim | Operational improvement |
|---|---|
| Sales visibility | Pipeline, forecast, targets and follow-up discipline by direction and person |
| Daily focus | One capped Morning Brief per person instead of scattered alerts |
| Preserve commercial commitments | Which proposal and terms were accepted, what changed, and what delivery and billing follow |
| Coordinate delivery | Every won sale has an accountable project, split into delivery batches, with a clear handover to accountants |
| Prevent missed or wrong charges | Billed and accrued amounts calculated from agreed terms and official delivery dates; visible overrides; renewal acceptance and quotes on time; billing-change alerts |
| Anticipate renewals | Renewal tenders for prepaid terms appear six months ahead, with expected revenue |
| Reduce fragmented records | Connected history, documents, decisions and responsibilities across modules |
| Protect sensitive information | Default deny; each role sees only its authorized records, actions and fields |
| Supplier-cost visibility *(later release)* | Estimates vs actuals and margin after supplier costs |

Numerical targets and detailed metric definitions remain to be set.

## 4. Modules and responsibilities

| Area | Owns | Connects through |
|---|---|---|
| **CRM** | Opportunities from Lead to Won/Lost (types: New customer, Expansion/Upsell, Renewal tender), the shared pipeline, one-off amounts, recurring lines, related deals, activities, tasks, targets, forecasts | Shared customers and contacts; Won handover with the signing date; Google Workspace; Upsell leads and Renewal tenders from Billing |
| **Commercial** | Proposal revisions, purchases, agreements, revenue lines with recurring terms, one-off breakdown, advance terms, amendments, discount and payment-term exceptions | The accepted scope, prices and terms used by PM and Billing |
| **Project management** | Projects (including projects with no sale value), templates, tasks, milestones, delivery batches and their allocations, handover, cancellation review | The source won opportunity and the exact batch delivered |
| **Billing** | Recurring contracts and settings, presets and joining rules, contract years, billed items, accrual items, renewal acceptance, annual quotes, advances and offsets, prepaid terms and renewal forecasts, handovers, adjustments | Accepted terms, official delivery dates per batch, CRM for Upsell leads and Renewal tenders |
| **Shared foundation and reporting** | Identities, role grants, configurable lists, GEL rates, documents, history, notifications, Morning Brief, dashboards | Stable links and consistent rules across modules |
| *Supplier costs (later)* | Suppliers, estimates, actuals, allocations, margin after supplier costs | Projects, management reporting |

Commercial is not an invoicing or accounting module. A shared customer view assembles all modules within the viewer's permissions.

## 5. The common business lifecycle

1. **Develop the opportunity.** A salesperson creates it in stage Lead, with a next action, and moves it through the shared pipeline.
2. **Record the accepted sale.** On Won, the salesperson enters the **contract signing date**, identifies the accepted proposal and terms (including the advance and the recurring terms), and chooses the delivery type. Any advance is invoiced at signing, outside the system.
3. **Plan and deliver.** One project per won opportunity, from the direction × delivery-type template, with the direction's default PM, or the deal Owner (flagged) until default PMs are named. The PM splits it into **delivery batches**, each carrying its share of the one-off amount and of the recurring items.
4. **Hand over each batch.** The PM marks a batch Delivered and sends it to the accountant. The accountant enters the **official delivery date**: the date the handover document was signed off on the Revenue Service portal.
5. **Bill and accrue.** Each batch is invoiced: its one-off share plus year-1 recurring, minus its advance offset. Its recurring items join the customer's contracts by their joining rules. Each contract then runs by contract year: acceptance, quote, accruals and billed items. Charges are handed over for external invoicing.

Later purchases (Upsells) and amendments link back without erasing earlier commitments. A change to agreed quantities or prices after Won, including during delivery, is an amendment: CRM keeps the sold values, and PM re-balances the batches not yet officially delivered. Renewals continue inside Billing, except renewals by tender, which return to CRM as Renewal tenders: automatically for prepaid terms, or created by a salesperson for other tender-based renewals.

| Concept | Meaning |
|---|---|
| Opportunity | A potential sale from Lead to Won/Lost; not an agreement or invoice |
| Stale | A deal whose next action is overdue or missing; there is no fixed idle-day rule |
| Nurture / Postponed / Cold | Paused states with a revisit date, a return date, or confirmation after 90 idle days |
| Related deals | Opportunities in different directions for one combined purchase; each keeps its own value, outcome and project |
| Won | Salesperson-confirmed sale **with a signing date**; documents optional; approvals separate; only a direction manager can revert it |
| Delivery batch | Part of a project with its own allocations, official delivery date and invoice; hardware-first deliveries, partial deliveries and milestones are batches |
| Delivered | PM confirmation of operational completion for a batch |
| Official delivery | The Revenue Service sign-off date, entered by the accountant; it drives billing and accrual |
| Project closed | Operational work is complete; accounting and billing work may continue |
| Renewal | Continuation of a recurring contract; handled in Billing, never a CRM opportunity, except a **Renewal tender** (automatic for prepaid terms, manual for other tender-based renewals) |
| Accrued / billed / paid | Earned in a period / asked of the customer (handed over for invoicing) / received (outside the system) |
| Charge Done | Checked and handed over for external invoicing; not an issued or paid invoice |

## 6. Core module rules to preserve

### CRM (CRM_Module_v3.3.md)
- One shared customer identity; one account owner per direction; lean account and contact fields; a configurable industry list; an optional parent account.
- One Owner per deal, reassignable by the direction manager.
- A next action is required at creation, stage change and reactivation; otherwise the deal is flagged.
- Stage-default probability, with an override that resets on stage change.
- A one-off amount (optional HW/SW/PS split) and recurring lines (Type, Name, 12-month amount, Currency), always shown separately.
- Lost needs a listed reason; Won needs the **signing date**; Won's reason is optional.
- **Won locks the sold amounts**; later changes are Commercial amendments.
- Each deal shows a generated summary and its flags: missing or overdue next action, expected close passed, contact coverage (no customer contact, or only one when the one-off or the 12-month recurring amount exceeds the direction's threshold, 1,000,000 GEL by default).
- **Renewal tender** opportunities are created automatically six months before a prepaid term ends; salespeople can also create them manually for other tender renewals.
- **No costs or margins in CRM.**
- Calendar meetings sync automatically (admin-connected, 24-month backfill, metadata only, private events excluded). Emails are logged on demand with the full body. The system never sends email.
- The dashboard covers sales won, targets, pipeline and forecast, win rate and time to close, follow-up discipline and activity volume.

### Commercial (Commercial_Module_v3.2.md)
- Proposals are prepared externally; revisions and structured terms are kept, and the accepted revision is identified.
- The three recurring revenue types are fixed. There is **no product catalogue**.
- The accepted terms record the signing date, the advance (0–100%) and the recurring terms for each line's joining rule.
- Amendments carry effective dates, and every change after Won is one, including during delivery. The deal Owner, the direction manager or the project's PM records them. Pre-sale approval covers only discount and payment-term exceptions.
- The one-off breakdown is HW / SW / PS in every module.
- A new recurring type or new one-off scope is an Upsell; a won Renewal tender is a new purchase.

### Project management (PM_Module_v3.3.md)
- Template checklists with target durations; the delivery type is chosen at Won.
- **Delivery batches** carry the one-off and recurring allocations, which must add up to the contract totals.
- Send to accountant / Take back per batch. Projects with no sale value handle launches without a sale.
- After an amendment, the PM re-balances the batches not yet officially delivered.
- Team members self-assign tasks and PMs can override.
- Cancellation review on a Won reversal, with nothing deleted. Closure once every batch is Delivered.
- Dependencies, effort and workload are deferred; Jira comes later, and Jira completion is never official delivery.

### Billing (Billing_Module_v3.6.md)
- **Vocabulary:** accrued, billed, paid. The system manages billed amounts, shows accruals, and never records payments.
- **One recurring engine.** Every contract has an accrual pattern, a billing pattern and an anniversary, with presets per product.
- **Four joining rules:**
  - After year 1 (Qmatic Care).
  - Units from the delivery month (SLA).
  - Aligned to the anniversary (SaaS).
  - Prepaid term with renewal by tender (HSM maintenance).
- **CEM Care:** year 1 is billed and accrued at official delivery with the project. Then the annual Care total per contract year. Renewal acceptance is always required 4–3 months before the anniversary; the annual quote goes 1 month before.
- **SLA:** units × price from the month of official delivery; free months are possible.
- **SLA and SaaS renewal:** acceptance is needed unless the contract auto-renews, due by the cancel-by date, with reminders 60 and 30 days before it.
- **SaaS:** the first project sets the anniversary; later projects and added users are billed for the months up to the anniversary.
- **Batches and advance:** each batch has its own invoice. The advance is 0–100% of the one-off total plus year-1 Care, offset proportionally by default.
- Done is a handover; corrections are linked adjustments; the last month of a contract year takes the rounding.
- Each recurring contract records its number, term, notice period and cancel-by date. The accountant can attach the handover document at official delivery.
- Due items not handed over escalate to the Executives after 5 working days. Prepared emails go through the outbox; an Admin names the approvers per email type.

### Supplier costs (Costs_Module_v2.md, deferred)
Direction managers would maintain post-Won estimates and actuals for supplier hardware, licences and subscriptions. The measure is margin after supplier costs, visible only in Costs and management reporting. The design is kept and returns in a later release.

## 7. Shared financial meaning and currencies

- Original amounts and currencies are kept everywhere; lines within one purchase may use different currencies.
- **Consolidated reports are in GEL**, at manually entered average rates **per calendar month**, maintained by direction managers. Corrections apply to new entries only; existing conversions keep their basis.
- CRM: open deals convert at the latest monthly rate; Won deals are frozen at their won-month rate. A missing rate is shown as unavailable, never as 1:1.
- Billing: charges stay in the agreement currency; conversion to the invoice currency is external.
- **Never add together** forecasts, accepted sales, billed amounts, accrued amounts and cash.
- Advances, batches and milestones divide an agreed amount; they are not additional sales. Renewals create no new sales value in CRM, except a won Renewal tender, which is a new sale. The CRM recurring measure is the first 12 months per line.
- The accounting system is **1C**.
- Still open: tax presentation; the accounting treatment of prepaid periods accrued at delivery (to confirm with the accountant); whether 1C can export invoice and payment status.

## 8. Shared access and data ownership

| Role | Scope |
|---|---|
| Salesperson | All deals and sales values in their own directions; edits their own |
| PM / Ops | Assigned projects, including sales values; manages batches and handover |
| Billing / Accountant | Agreements, recurring contracts, billed and accrued items, batches awaiting official delivery, across directions |
| Direction manager | Everything in their directions |
| Executive | Everything, all directions (view) |
| Admin | Users, role grants, settings; no automatic financial visibility |
| No role (task-only) | Own assigned tasks, with the linked record's name |

- Roles are explicit grants with direction scopes. A job title grants nothing. **Default deny**: grants are widened explicitly and logged.
- Multiple roles combine, each within its own scope. Viewing, editing, approving and sharing are separate rights.
- Only the CEO or designated administrators grant cross-direction sharing, and recipients keep their financial restrictions.
- **Direction managers** edit shared customer identity, merge duplicates, configure their pipeline options and the contact-coverage threshold, revert Won, set targets, maintain GEL rates and view the briefs of people in their directions. *Proposed:* they also decide when renewal acceptance is missing. Executives view anyone's brief; Admin alone cannot.
- **Billing / Accountant** enters official delivery dates, records acceptance, sends annual quotes, sets contract settings and overrides advance offsets.
- **Amendments** are recorded by the deal Owner, the direction manager or the project's PM.
- The same restrictions apply to reports, search, exports, APIs, notifications, attachments, activity history (including logged email bodies) and integration payloads. Hidden records never enter totals. See Access_and_Permissions_v3.3.md.
- Logged activities are edited by their author, and by direction managers in their directions; deletions keep a trace. Executives see the whole audit log; Admin sees access entries only.

## 9. Shared architecture and integrations

- **PostgreSQL** with row-level security, server-side field and aggregate checks, and server-side reporting.
- A modular monolith in **TypeScript**, built fresh. The prototype is the test bench and UI reference and never holds real data.
- Code lives in an NGT-owned repository, with CI.
- **A background worker runs all scheduled work**, retry-safe: contract years, acceptance windows, quotes, renewal-tender alerts, reminders, sync and imports.
- **Open:** hosting, data residency and authentication. Google Workspace sign-in is the working assumption.

**Principles:**
- Stable links from customer to opportunity, terms, project, batch and charge.
- Traceable revisions, effective dates, events and actors.
- Retry-safe events, syncs and imports.
- Every system-prepared email goes through the approval-gated outbox (Arch 19); the system never sends email.
- Source facts kept separate from derived forecasts, conversions and calculations. Every billed and accrual item stores its calculation.
- Configurable variation (settings, presets, joining rules) without disconnected records.

**Google Workspace:**
- The primary calendars of all CRM users are read through admin domain-wide access. Meetings match CRM contacts or account domains; internal-only and private events are excluded.
- Metadata only, with 24 months of history, and automatic deal linking when unambiguous.
- Gmail: "Log to CRM" add-on or BCC; the full body is stored and attachments are linked.
- No calendar write-back except optional task due dates.

**Jira** (later): two-way integration for development and installation tickets. Compatible changes are kept, conflicts are flagged for the PM, and Jira completion is not official delivery.

## 10. Existing data and transition

The app replaces HubSpot and the relevant monday.com workflows, not everything in those platforms. monday.com is a migration source only, and its replaced boards become read-only.

- Import active records and the history they need, with attachments. For CRM, all closed Won/Lost history is also imported and mapped to the shared pipeline.
- Suggested duplicates need a designated reviewer's confirmation before import. After go-live, direction managers merge.
- Each data type has one primary source, and conflicts are reviewed manually.
- Incomplete records wait in a review queue until their essential fields are complete.
- For Billing, each contract's settings and joining-rule inputs (including official delivery dates), the current contract year, and open projects' batches and advances are imported.
- Historical states never replay events. Imported Won deals create no projects and need no signing date; handovers, acceptances and quotes are never fabricated.
- Modules go live individually, with all intended users together, after the CEO confirms readiness. The old workflow then becomes read-only.
- Before build, the aligned prototype is used for 3–4 walkthrough sessions with salespeople, a PM and an accountant; their findings update the documents. On 27 September 2026 the prototype was not yet aligned; NGT_CRM_Gap_Register tracks what remains.

Details: Shared_Data_and_Migration_v3.1.md and Monday_Migration_Mapping_v1.md.

## 11. Product boundaries

**Not in the first release:**
- Supplier costs and margin.
- The lead inbox and web forms.
- Invoice sent/paid tracking and receivables (a read-only paid flag may come later).
- The account health score.
- A user-editable automation engine, custom fields and a report builder.
- Service tickets (where support lives is open).
- PM dependencies, rescheduling, effort and workload.
- Jira.
- The dedicated accounting page.
- The international VOIX partner model.
- Type 3 (large public) Care.

**Permanently outside the product unless explicitly decided:**
- Accounting, invoice or credit-note generation, payment collection and reconciliation.
- Supplier purchase orders, supplier invoices and payables.
- Stock, warehouses and serial-number inventory.
- **Product catalogues and in-app proposal generation** (Commercial 7).
- Pre-sale supplier-cost estimating, and any costs or margins in CRM.
- Time logging, labour costing, payroll and overhead allocation.

Expanding any boundary is a separate, explicit decision.

## 12. How to use this context in a module conversation

Attach this brief and the relevant module document at its current version. Treat the module document as the detailed baseline and this brief as the shared context.

When refining a module:
1. Separate confirmed, proposed and open items.
2. Develop roles, records, screens, workflows, rules, exceptions and acceptance examples. Use worked numbers wherever money is involved.
3. For each cross-module connection, state the source data, receiving module, responsible role, trigger and change behaviour.
4. Preserve shared meanings (including accrued, billed and paid), financial restrictions and boundaries. Flag proposed changes to other modules rather than assuming them.
5. Prefer the newest explicit decision, and surface unresolved conflicts between documents.
6. Ask focused questions, mostly multiple-choice with a recommendation. Don't reopen settled choices without a concrete reason.
7. Refine functionality before choosing technology or delivery priorities.
8. When a module is updated, save a new version with a "Changes from previous version" table. **Keep still-valid content; do not condense it away.** Update the prototype through a change request so the test bench stays aligned.

**Suggested opening request for a new chat:**

> Use the attached Project Context and Aims v3.3 as the shared context and the attached module description as the detailed baseline. Help me refine this module into clear functional requirements, including workflows, screens, records, rules, exceptions and connections to the other modules. Start by identifying the most consequential unresolved issues, then ask focused questions, mainly multiple-choice with your recommendation. Preserve confirmed decisions, distinguish new proposals from agreed requirements, and flag cross-module impacts.

**Sources:** NGT_Project_Context_and_Aims_v2.md and v3; the current module documents; the NGT CRM prototype's PROCESSES.md and ARCHITECTURE.md; change request CR-2026-09; decisions confirmed by the CEO on 25–27 September 2026; the prototype gap review (NGT_CRM_Gap_Register, 27 September 2026); the CEO's answers to the open questions of change request CR-2026-09 rev. 4 (28 September 2026).
