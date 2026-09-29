# NGT Group — CRM Module
**Functional draft 3.3 · 28 September 2026 · supersedes CRM_Module_v3.2.md**

**v3.3 records the CEO's answers to the open questions** raised while preparing change request CR-2026-09 rev. 4 (28 September 2026). Decided:
- The seeded pipeline probabilities and optional stages are accepted as the starting defaults.
- The contact-coverage threshold is 1,000,000 GEL per direction, and direction managers can change it.
- Salespeople can also create Renewal tenders manually.
- The Morning Brief gains an "Emails to approve" section.
- An overall company status is shown, derived from the directions.
- Direction managers and Executives can view other people's briefs (Access 24).

Everything else in v3.2 stands. The v3.2 introduction follows.

**v3.2 adopts rules from Luka Geldiashvili's prototype**, found in the gap review of 27 September 2026 (NGT_CRM_Gap_Register, rows P-01 to P-29) and confirmed by the CEO. The prototype had these rules; v3.1 didn't cover them:
- Won locks the deal's sold amounts; later changes are Commercial amendments.
- A generated deal summary and two more deal flags.
- Task reminders, personal tasks, the Morning Brief's "seen" marker and a suggested first next action.
- Sales analysis, including recurring growth.
- Editing your own logged activities, scoped global search, a derived customer status per direction and ID-number lookup.

The one-off split stays HW / SW / PS, and Commercial, PM and Billing now use it too.

Everything else in v3.1 stands. The v3.1 introduction follows.

**v3.1 aligns CRM with Billing_Module_v3.4** (the billing rules agreed on 26 September 2026). Two CRM rules change:
- Marking a deal **Won requires the contract signing date**, which starts the advance in Billing.
- A new opportunity type, **Renewal tender**, is created automatically when a prepaid maintenance term sold through a tender (HSMs) approaches its end. This is the one exception to "renewals never enter CRM".

Everything else in v3 stands. The v3 introduction follows.

v3 applied the decisions agreed in the review of Luka Geldiashvili's CRM prototype against the v2 design (25 September 2026). It simplifies lead intake and pipelines for a team of about ten, adopts several prototype features that v2 lacked, and names the six directions consistently. The same rules are sent to the prototype as change request CR-2026-09, so the prototype can serve as the test bench for these workflows.

It is a functional design, not implemented software. Where this document and CRM_Module_v2.md disagree, this document takes precedence. CRM 1–61 stand unless the tables below revise, defer or supersede them.

## Changes from v3.2 (v3.3)

| Area | v3.2 | v3.3 | Ref |
|---|---|---|---|
| Seeded pipeline | To be confirmed by each direction manager before go-live | Accepted as the starting defaults; direction managers still adjust them (CRM 66) | CRM 96; §6a |
| Contact coverage | Threshold proposed at 50,000 GEL | **1,000,000 GEL** per direction by default, on the one-off or the 12-month recurring amount separately; direction managers set it for their direction | CRM 87 (decided); CRM 66 |
| Renewal tender | Automatic; manual creation proposed | Salespeople can also create one manually, linked to the original purchase | CRM 83 (decided) |
| Morning Brief | Sections as in §3 | Adds **Emails to approve** for each email's recipients and designated approvers | CRM 97 |
| Other people's briefs | Proposed in Access 24 | Direction managers for people in their directions, Executives for anyone; Admin alone cannot | CRM 98; Access 24 |
| Customer status | Per direction | Also an **overall company status**, derived from the directions, for display only | CRM 94 (refined) |
| Cross-references | Some pointed to v3.1 documents | Point to the current set | §11–13 |

## Changes from v3.1 (v3.2)

| Area | v3.1 | v3.2 | Ref |
|---|---|---|---|
| Won deal | Not stated whether amounts can change after Won | One-off amount and split, recurring lines, currencies and direction are read-only after Won; changes are Commercial amendments | CRM 85 |
| Deal summary | Not in CRM (kept by CR-28) | Generated one-line summary on every deal | CRM 86 |
| Deal flags | Missing or overdue next action | Adds **Expected close passed** and **Contact coverage** | CRM 87 |
| Tasks | Owner, due date, purpose, status | Adds a reminder date and personal tasks | CRM 88 |
| Morning Brief | Status changes first | A per-person "seen" marker sets the status-change window | CRM 89 |
| First next action | Required, typed by the creator | Prefilled suggestion "Qualify {account}: …", due in 5 days | CRM 90 |
| Sales dashboard | §9 measures | Adds a stage funnel, the Lost-reason breakdown and recurring growth (won vs started) | CRM 91 |
| Logged activities | No edit rule | The author edits or deletes their own; deletions keep a trace | CRM 92 |
| Search | Scope rule only | Global search across accounts, opportunities and contacts, within permissions | CRM 93 |
| Customer status | — | Derived per direction: Prospect / Active / Former | CRM 94 |
| ID number | Shared identity (Data 3) | Lookup and autofill on a new opportunity; edits stay with direction managers | CRM 95 |
| Offboarding | The last administrator can't be removed | Nobody can remove their own account either | CRM 78 (refined) |
| One-off split | HW / SW / PS in CRM | HW / SW / PS in every module; licences count as SW; installation, configuration and custom development count as PS | CRM 69 (confirmed); Commercial 13; PM 20 |

## Changes from v3 (v3.1)

| Area | v3 | v3.1 | Ref |
|---|---|---|---|
| Won | Salesperson confirms Won, identifies accepted terms, chooses delivery type | Also **requires the contract signing date**; it sets up the advance record in Billing | CRM 81 |
| Opportunity types | New customer, Expansion/Upsell | Adds **Renewal tender**, created automatically 6 months before a prepaid maintenance term ends | CRM 82–83 |
| Renewals | Never CRM opportunities | Still true, **except renewals by tender of prepaid terms** | CRM 82 |
| Recurring lines | 12-month amount per line; Billing templates calculate | Unchanged in CRM. The billing details (joining rule, settings, users, prepaid years, advance) are captured in Commercial and Billing. | CRM 84 |

## Changes from v2

| Area | v2 | v3 | Ref |
|---|---|---|---|
| Direction names | Digital signage, VOIX | **Digital Signage**, **VOIX + CF** (CF = Customer Feedback); Kiosks kept | CRM 62 |
| Lead intake | Separate inbox per direction, Unsorted queue, self-claim, visual aging | **Lead is the first pipeline stage.** Inbox, Unsorted and claiming are deferred until web forms exist. | CRM 63 |
| Nurture | Lead outcome | **Paused state** available from Lead or Qualified, with a revisit date | CRM 64 |
| Pipelines | Six independently configured pipelines, seeded per direction | **One shared default pipeline** with optional Tender/Procurement and PoC/Pilot stages per direction | CRM 65 |
| Pipeline configuration | Stages, probabilities, required fields per stage, lost reasons, Cold threshold | Toggle optional stages, adjust probabilities, lost reasons, Cold threshold. **Custom stages and required fields per stage are deferred.** | CRM 66 |
| Ownership | Creator or claimer | Creator, reassignable by the direction manager; "Created by" kept | CRM 67 |
| Revenue timing | Expected close month only | Adds an optional **expected delivery month** | CRM 68 |
| One-off amount | Single amount, no breakdown | Single amount with an **optional HW / SW / PS split**; a labelled derived "First-year value" may be shown | CRM 69 |
| Duplicate deals | Not covered | **Warning** on a second open deal for the same account and direction | CRM 71 |
| Targets | Not covered | **Sales targets per owner** per year | CRM 72 |
| Daily view | My work plus a daily email digest | **Morning Brief** as the home screen, capped at 10 items | CRM 73 |
| Productivity | — | Meeting-notes parser, prepared email templates, cross-sell hints, account signals | CRM 74–77 |
| Offboarding | Only "Former employee" at migration | **Offboarding flow** reassigns everything a departing user owns | CRM 78 |
| First-release exclusions | — | Invoice paid tracking, health score, catalogue and quotes, automation-rule editor, custom fields, report builder and service tickets are excluded | CRM 80 |

### Refinement round I — open questions answered (28 September 2026)

| Ref | Decision |
|---|---|
| CRM 96 | **Seeded pipeline accepted.** The probabilities and optional stages in §6a are the starting defaults for every direction. Direction managers adjust them for their direction (CRM 66); changes are logged. |
| CRM 87 (decided) | **Contact-coverage threshold: 1,000,000 GEL** by default, per direction. It is compared with the deal's one-off amount and, separately, with its 12-month recurring amount, both in GEL. The Direction manager can change it for their direction (CRM 66). A deal with no customer contact is flagged at any value. |
| CRM 83 (decided) | **Manual Renewal tenders.** Besides the automatic creation for prepaid terms, a salesperson can create a Renewal tender opportunity manually for any other renewal that goes through a tender (for example public-sector Care), linked to the original purchase. It follows the normal pipeline and direction scope (Access 20). |
| CRM 97 | **"Emails to approve"** is a Morning Brief section. Each email the system has prepared (Solution Architecture, Arch 19; Billing 62) appears in the brief of its recipients and designated approvers until it is sent or discarded. *Adopted from the prototype.* |
| CRM 98 | **Viewing other people's briefs** (Access 24, decided). A direction manager can view, read-only, the briefs of people whose grants are in their directions; an Executive can view anyone's. Admin alone cannot. A viewed brief shows only what the viewer's own grants allow. Only the person marks their brief as seen (CRM 89). |
| CRM 94 (refined) | An **overall company status** is shown next to the per-direction statuses, derived from them: *Active* if any direction is Active, otherwise *Former* if any direction is Former, otherwise *Prospect*. It is for display and filtering only and is never entered. |

### Refinement round H — prototype gap review (27 September 2026)

| Ref | Decision |
|---|---|
| CRM 85 | **Won locks the sold amounts.** Once a deal is Won, its one-off amount and HW / SW / PS split, its recurring lines, their currencies and the direction are read-only in CRM. They stay as sold for sales reporting and targets. A change agreed with the customer afterwards is recorded as an amendment in Commercial (Commercial 16), which updates the contract totals that PM and Billing use. Fields that don't change the sale (next action, tasks, contacts, notes, related-deal links) stay editable. If a direction manager reverts Won (CRM 30), the deal becomes editable again. *This was the prototype's documented rule ("the deal is never changed after the sale"), which its code doesn't yet enforce.* |
| CRM 86 | **Deal summary.** Every opportunity shows a generated one-line summary: stage and days in it, one-off and 12-month recurring values, effective probability, the next action and its due date, the last real interaction, open tasks, the number of customer contacts and any flags. It is rule-based, not AI, and is never stored. |
| CRM 87 | **Two more deal flags**, next to "Missing next action" and "Overdue next action":<br>• **Expected close passed**: the expected close month is over and the deal is still open.<br>• **Contact coverage**: the deal has no customer contact, or only one while its one-off amount or 12-month recurring amount is above the direction's threshold (1,000,000 GEL by default, decided in round I).<br>Flags show on the board, list and deal page and in the Owner's Morning Brief. They are not "stale" (§6) and don't affect the Cold clock. The prototype's other risks are not adopted: "60+ days in stage" is an idle-day rule, and "customer has unpaid invoices" is outside the boundary (CRM 80). |
| CRM 88 | **Task reminders and personal tasks.** Any task can carry a reminder date; on that date it appears under Reminders in the assignee's Morning Brief. Users can also create personal tasks linked to no account or opportunity; only their owner sees them. |
| CRM 89 | **"Seen" marker.** Each person marks their own Morning Brief as seen. Status changes are those since their last mark; before the first mark, the last 7 days. Only the person can mark their brief. Marking clears status changes only; every other section stays until it is resolved. |
| CRM 90 | **Suggested first next action.** A new opportunity's required next action is prefilled as "Qualify {account}: budget, timeline, decision maker", due in 5 days. The Owner can change the text and the date. This replaces the prototype's editable "new deal" automation rule; there is no rule engine in the first release (CRM 80). |
| CRM 91 | **Sales analysis.** The sales dashboard (§9) adds:<br>• a stage-conversion funnel;<br>• the Lost-reason breakdown by direction and competitor;<br>• win rate and time to close by direction;<br>• **recurring growth**: 12-month recurring value won, by month won, next to recurring started, by month of official delivery (from Billing), with running totals and a table view.<br>One-off and recurring stay separate, and sold and started values are never added together. |
| CRM 92 | **Editing logged activities.** The person who logged a note, email, call or meeting can edit or delete it; direction managers can in their directions. A deletion keeps a trace in the record's history and in the audit log. The stage log is never editable. Admin alone gives no right (Access 21). |
| CRM 93 | **Global search** (Ctrl+K) finds accounts by name or ID number, opportunities by ID, title or account, and contacts by name, email or phone, from the account's contact directory. Results follow the searcher's permissions (CRM 79, Access 23). |
| CRM 94 | **Customer status per direction** is derived, never entered: *Prospect* (no Won deal in that direction), *Active* (an active agreement or recurring contract, or a project in delivery) or *Former* (had one, none now). It shows on the account, and cross-sell hints (CRM 77) use it. |
| CRM 95 | **ID-number lookup.** On a new opportunity, choosing a known account shows its ID number, and typing an ID number finds the account. Changing an account's ID number stays a direction-manager action (Data 3); a new opportunity never overwrites it. |
| CRM 78 (refined) | Nobody can remove their own account, in addition to the last-administrator rule. |
| CRM 69 (confirmed) | **HW / SW / PS is the one-off split in every module.** Licences count as software; installation, configuration and custom development count as professional services. Commercial 13 and PM 20 now use the same split. |

### Refinement round G — alignment with Billing v3.4 (26 September 2026)

| Ref | Decision |
|---|---|
| CRM 81 | **Won requires the contract signing date.** The salesperson enters it when marking a deal Won. Billing uses it to record the advance (0–100% per contract, Billing 49 and 59); the advance invoice itself is issued outside the system. Imported historical Won deals are exempt. |
| CRM 82 | **Renewal tender** is a third opportunity type, next to New customer and Expansion/Upsell. It exists because, for prepaid maintenance sold mainly to public institutions (HSMs), each renewal is a separate tender: a real sale that can be lost. Renewal tenders (automatic for prepaid maintenance, manual for other tender-based renewals, CRM 83) are the **only exception** to CRM 19/48. Every renewal that doesn't go through a tender stays in Billing. |
| CRM 83 | **Automatic creation.** Six months before a prepaid maintenance term ends (Billing 58), the system creates a Renewal tender opportunity:<br>• direction and account of the original sale;<br>• Owner: that direction's account owner, or else the direction manager;<br>• stage Qualified;<br>• a Maintenance recurring line whose 12-month amount equals the original one-year maintenance value;<br>• expected close date at the end of the coverage;<br>• a next action for the Owner.<br>The account owner and the direction manager are alerted. Salespeople can also create a Renewal tender manually for other tender-based renewals (decided in round I). |
| CRM 84 | **CRM records sales measures only.** Recurring lines keep Type, Name, 12-month amount and Currency. For per-user SaaS, the 12-month amount is users × annual price. For prepaid multi-year maintenance, it is the one-year value. The billing details (joining rule, accrual and billing settings, anniversary, users, prepaid years, advance percentage) are captured at acceptance in Commercial and held in Billing. |

## 1. Decision record

### Status of earlier decisions

| Ref | Decision | v3 status |
|---|---|---|
| CRM 1, 14 | Separate lead inbox; full inbox with Converted, Disqualified, Nurture | **Deferred** by CRM 63. Returns with web forms. |
| CRM 2–3 | Qualification by judgment; account owner per direction | Kept |
| CRM 11 | Calendar auto-logged; email on demand | Kept |
| CRM 12 | Related deals | Kept |
| CRM 13, 47, 54 | Configurable pipeline per direction; seeded six-stage pipelines | **Superseded** by CRM 65 |
| CRM 15–21 | Next action, probability override, recurring types, paused states, opportunity types, dashboard, recurring line fields | Kept (dashboard extended by CRM 72) |
| CRM 22–25 | Lead sources, self-claim, direction inboxes, visual aging | **Deferred** by CRM 63 |
| CRM 26 | Creator or claimer owns the opportunity | **Refined** by CRM 67 |
| CRM 27–31 | Lost reasons, Cold suggestion, Postponed return, reopen/revert, no costs in CRM | Kept |
| CRM 32 | Single one-off amount, no breakdown | **Revised** by CRM 69 (optional split) |
| CRM 33 | Required fields per stage | **Deferred** by CRM 66 |
| CRM 34 | Direction managers configure their pipeline | **Narrowed** by CRM 66 |
| CRM 35 | Salespeople see all deals in their direction, edit their own | Kept |
| CRM 36 | Anyone routes Unsorted leads | **Deferred** with CRM 63 |
| CRM 37 | Nurture needs a revisit date | Kept, now as a paused state (CRM 64) |
| CRM 38–46 | Duplicates, activity types, Cold default 90 days, partner deals, meeting credit, fields, parent account, currency, lost-reason list | Kept |
| CRM 48 | Upsell vs renewal | Kept. The Upsell lead now lands as a Lead-stage opportunity (§5). |
| CRM 49 | Notifications | **Revised** by CRM 73 (Morning Brief replaces My work and the daily digest) |
| CRM 50–61 | Migration, tasks, web forms deferred, industry list, Google sync | Kept. CRM 50's stage mapping is re-pointed to the shared pipeline (§14). |

### Refinement round F — prototype review (25 September 2026)

| Ref | Decision |
|---|---|
| CRM 62 | **Six directions:** CX / Queue management (Qmatic); Digital ID / Security; Cash handling; Digital Signage; VOIX + CF (Customer Feedback); Kiosks. |
| CRM 63 | **Lead is the first pipeline stage.** A lead is an opportunity in stage Lead (5%), created manually by any salesperson or manager in a chosen direction. The separate lead inbox, Unsorted queue, self-claim and inbox aging are deferred until web forms exist. While in Lead or Qualified, the owner or direction manager may move the deal to another direction; the move is logged. |
| CRM 64 | **Nurture** is a paused state available only from Lead or Qualified. It requires a revisit date. On that date the deal returns to its owner's Morning Brief. |
| CRM 65 | **One shared default pipeline:** Lead 5%, Qualified 10%, Solution/Demo 25%, Proposal sent 50%, Negotiation 75%, Contract signing 90%, then Won/Lost. **Optional stages** per direction: Tender/Procurement 60% (after Proposal sent) and PoC/Pilot 35% (after Solution/Demo). |
| CRM 66 | **Direction managers** switch their direction's optional stages on or off, adjust default probabilities, maintain lost reasons and set the Cold threshold and, since v3.3, the contact-coverage threshold (CRM 87). Changes are logged. Custom stages and required fields per stage are deferred. The creation minimum plus a next action applies to every stage. A stage can be switched off only when no open deal sits in it. |
| CRM 67 | **One accountable Owner.** The creator becomes Owner. Direction managers can reassign it; reassignment is logged and notifies the new Owner. "Created by" is kept as read-only history. The Owner gets the sales credit in targets, dashboards and the brief. |
| CRM 68 | **Expected delivery month** is an optional field. It drives revenue-timing views. There is no separate delivery probability. |
| CRM 69 | The one-off amount may optionally be **split into hardware, software and professional services**, and the split must sum to the amount. A derived **First-year value** (one-off plus the 12-month recurring amounts) may be displayed, always labelled as such, and is never stored or reported as a sales measure. |
| CRM 70 | Marking **Won** takes an optional reason. Lost keeps its required listed reason (CRM 27). The seeded lost-reason list gains **Not qualified**, which replaces the old Disqualified lead outcome. |
| CRM 71 | Creating an opportunity when an **open deal already exists for the same account and direction** gives a warning with a link to it. Creation is not blocked. |
| CRM 72 | **Sales targets** per Owner per calendar year: won one-off value and won 12-month recurring value, in GEL. Direction managers set them for their direction, executives for everyone. Dashboards show progress. |
| CRM 73 | **Morning Brief** is the home screen for every user. It is capped at 10 items, puts status changes first, and rotates the remaining slots fairly across sections. Each section shows its full count. It replaces My work and the daily email digest. Instant alerts (reassignment, Won/Lost) and the weekly manager summary remain. |
| CRM 74 | **Meeting notes** pasted on a deal become a note. `TODO:` lines become tasks, `@Name` assigns them and `by <date>` sets the due date. The parser is rule-based. |
| CRM 75 | **Email templates** with merge fields prepare an email. A person opens it in their own mail app, sends it, and logs it. The system never sends email automatically. |
| CRM 76 | Accounts show plain **signals**: last real interaction (with days), open deals, overdue or missing next actions, renewals due or overdue, and projects in cancellation review. There is **no composite health score**. |
| CRM 77 | Each account shows **cross-sell hints**: directions in which it has no deal or active agreement. |
| CRM 78 | **Offboarding:** when an administrator removes a user, the system lists everything they own (open deals, account-direction ownership, open tasks, default-PM settings, role grants). The administrator names a successor for each group. Everything moves together, the successor is notified, and history keeps the original name. The last administrator cannot be removed. |
| CRM 79 | **CSV export** of accounts and deals is available within the exporter's permissions. Hidden records never appear, and totals never include them. |
| CRM 80 | **Not in the first release:** invoice sent/paid tracking and receivables ageing, account health score, product catalogue and quote generation, a user-editable automation-rule engine, custom fields, a report builder, and service tickets. Each needs a separate decision to add. |

## 2. Purpose and boundary

CRM owns opportunities from Lead to Won/Lost, the shared pipeline and its per-direction options, sales activities, next actions, targets and sales-value forecasts. It hands a Won opportunity to Commercial and PM.

CRM does not own accepted agreements or amendments (Commercial), projects (PM), charges and renewals (Billing), or supplier costs and margins. **There are no cost fields, margin figures or cost-based indicators anywhere in CRM** (CRM 31). CRM does not record invoices or payments (CRM 80).

## 3. Workspaces

| Workspace | Purpose |
|---|---|
| Morning Brief | Home screen: status changes, notifications, next actions due or overdue, missing next actions, Cold suggestions, returning Postponed deals, Nurture revisits, meetings to assign to a deal, reminders, deal flags and emails to approve (CRM 73, 87–89, 97) |
| Pipeline | Board and list per direction, with stage, values, effective probability, Owner, next action and flags. Filters by direction, Owner, stage and flag. |
| Customers | Shared customer record: contacts, per-direction account owners, parent account, customer status per direction (CRM 94), signals (CRM 76), cross-sell hints (CRM 77), and a permission-filtered timeline |
| Tasks | The user's tasks, including personal tasks and reminders (CRM 88), by Overdue / Today / Next 7 days / Later, with a calendar view |
| Sales dashboard | Measures in §9, including target progress and sales analysis (CRM 91) |
| Search | Global search (Ctrl+K) across accounts, opportunities and contacts, within the searcher's permissions (CRM 93) |
| Settings (CRM) | Optional stages, probabilities, lost reasons and Cold threshold per direction (direction managers); targets; email templates; industry list |

## 4. Records

| Record | Content |
|---|---|
| Account | Fields per CRM 43, optional parent account (CRM 44) |
| Contact | Name, title, email, phone, account, role in deal, active flag |
| Account-direction owner | One account owner per account per direction |
| Opportunity | Direction, stage, state, type (New customer / Expansion-Upsell / Renewal tender), Owner, Created by, expected close date, optional expected delivery month, probability (default or override), **signing date (required for Won)**, flags; for Renewal tender, a link to the original purchase |
| One-off amount | Amount, currency, optional HW / SW / PS split (CRM 69) |
| Recurring line | Type (Care/Maintenance, SaaS, SLA), name, 12-month amount, currency (CRM 21) |
| Related-deal link | Cross-direction link with an optional group label |
| Activity | Synced meeting, logged email, call or note; edits and deletions keep a trace (CRM 92) |
| Task / next action | Owner, due date, purpose, status, optional reminder date; one marked as the designated next action. Personal tasks have no linked record (CRM 88). |
| Target | Owner, year, one-off target, recurring target (GEL) |
| Email template | Name, subject, body with merge fields |
| Configuration | Per-direction optional stages, probabilities, lost reasons, Cold threshold |
| History | Stage, owner, amount, date, direction and probability changes; overrides; reopen and revert reasons; activity edits and deletions |

## 5. Opportunity intake

1. **Create.** A salesperson or manager creates an opportunity in stage **Lead**, choosing account, direction, type (New customer, Expansion/Upsell, or Renewal tender linked to the original purchase, CRM 83), expected close date and a next action. The creator becomes Owner (CRM 67).
2. **Duplicates.** The system warns on likely duplicate accounts and contacts (CRM 38) and on an open deal for the same account and direction (CRM 71). Nothing is blocked.
3. **Qualify** by judgment (CRM 2) and move the deal through the stages.
4. **Not qualified.** Mark the deal Lost with the reason *Not qualified* (CRM 70).
5. **Park.** Put the deal into Nurture with a revisit date (CRM 64).

**Upsell leads from Billing** (CRM 48): a billing user raises the request from an agreement. It creates a Lead-stage Upsell opportunity in the requested direction. The Owner is the account owner for that direction, or the direction manager if there is none. The Owner is notified. The billing user gains no view of the opportunity.

**Renewal tenders** (CRM 82–83): created automatically six months before a prepaid maintenance term ends, in stage Qualified, with the original one-year maintenance value. If it is Lost, Billing stops forecasting the renewal revenue. If it is Won, it is billed as a new sale with its own prepaid term. A salesperson can also create one manually for another renewal that goes through a tender (for example public-sector Care), linked to the original purchase.

**Partner deals** (CRM 41): the account is the invoiced party.

## 6. Opportunity lifecycle

**States:** Active (in a stage), Nurture, Postponed, Cold, Won and Lost.

| Transition | Rule |
|---|---|
| Create | Account, direction, type, Owner, expected close date and next action are required. Probability takes the stage default. |
| Stage change | A next action is required. Any probability override resets to the new stage's default. |
| Next action completed with no replacement | Flagged "Missing next action". Not blocked. |
| Next action past its due date | Flagged "Overdue next action". This is the only meaning of "stale". |
| Lead/Qualified → Nurture | Revisit date required. The deal returns to the Owner's brief on that date. |
| Active → Postponed | Return date required. On that date the deal returns to its prior stage and the Owner is prompted for a next action. |
| Active → Cold | Suggested after N days without a real interaction (default 90, set per direction). The Owner confirms or snoozes, or sets Cold manually. |
| Nurture/Postponed/Cold → Active | Next action required. |
| → Lost | Listed reason required; competitor name optional when the reason is Competitor; note optional. |
| Lost → Active | The Owner reopens with a logged reason and a next action. |
| → Won | The salesperson enters the **contract signing date** (required, CRM 81), confirms Won optionally with a reason, identifies the accepted terms in Commercial, and chooses the delivery type for the project (see §11). The sold amounts are then locked (CRM 85). |
| Won → reverted | Direction manager only, with a reason. The project is flagged for cancellation review, not deleted. The deal's amounts become editable again. |

A **real interaction** (CRM 40) is a meeting held, a logged email, a logged call or a completed task. Notes and field edits do not count.

Nurture, Postponed and Cold deals are excluded from the weighted forecast and from the win-rate denominator. They stay visible in pipeline views and in follow-up discipline.

## 6a. Shared pipeline (CRM 65)

| Stage | Default probability | Default use |
|---|---|---|
| Lead | 5% | All directions |
| Qualified | 10% | All directions |
| Solution / Demo | 25% | All directions |
| PoC / Pilot *(optional)* | 35% | On by default for Digital ID / Security and VOIX + CF |
| Proposal sent | 50% | All directions |
| Tender / Procurement *(optional)* | 60% | On by default for CX / Queue management, Digital ID / Security, Cash handling and Kiosks |
| Negotiation | 75% | All directions |
| Contract signing | 90% | All directions |
| Won / Lost | 100% / 0% | All directions |

Stage order is Lead → Qualified → Solution/Demo → (PoC/Pilot) → Proposal sent → (Tender/Procurement) → Negotiation → Contract signing. Direction managers adjust the defaults (CRM 66). The CEO accepted the seeded values as the starting defaults on 28 September 2026 (CRM 96).

## 7. Opportunity value

Each opportunity has **one one-off amount** and **any number of recurring lines**.

- **One-off amount:** one amount and currency. The optional HW / SW / PS split must sum to it (CRM 69). A fuller breakdown belongs in the proposal and Commercial.
- **Recurring lines:** Type (Care/Maintenance, SaaS or SLA), Name (prefilled, editable), 12-month amount and Currency. Several lines of the same type are allowed. CRM calculates no recurring pricing; Billing's recurring engine does (Billing v3.6). For per-user SaaS, the 12-month amount is users × annual price; for prepaid multi-year maintenance, it is the one-year value (CRM 84).
- **After Won** the amounts are read-only; any later change is a Commercial amendment (CRM 85, Commercial 16).
- **Display:** one-off and recurring values are always shown separately. **New MRR** = recurring 12-month amounts ÷ 12, by type and in total. A labelled **First-year value** may appear on the deal page only.

## 8. Forecasting

- Effective probability is the override if there is one, otherwise the stage default.
- Weighted one-off forecast = one-off amount × effective probability.
- Weighted recurring forecast = 12-month recurring amount × effective probability, by type and in total.
- Forecasts are grouped by expected close month. A second view groups the one-off forecast by **expected delivery month**, with an "undated" bucket (CRM 68).
- GEL consolidation uses the monthly manual rates. Open deals use the latest month's rate. Won deals are frozen at their won-month rate (CRM 45). Original amounts are kept. A missing rate shows the original amounts and marks the GEL figure unavailable; it is never treated as 1:1.
- Related deals are counted once each. A group label never adds value.
- These are sales-value forecasts, not billing schedules or cash.

## 9. Sales dashboard

| Measure | Definition |
|---|---|
| Sales won | One-off amount and 12-month recurring amount by type, for deals won in the period |
| Targets | Progress of won one-off and won recurring value against each Owner's target (CRM 72) |
| New pipeline and forecast | Value of opportunities created in the period (one-off and recurring separately), and the current weighted forecast |
| Win rate and time to close | Won ÷ (Won + Lost) for deals closed in the period; average days from creation to Won |
| Follow-up discipline | Overdue next actions, missing next actions, Postponed deals past their return date, pending Cold suggestions, Nurture revisits due, deal flags (CRM 87) |
| Stage funnel and lost reasons | Conversion from each stage to the next; Lost reasons by direction and competitor; win rate and time to close by direction (CRM 91) |
| Recurring growth | 12-month recurring won, by month won, and recurring started, by month of official delivery, with running totals (CRM 91) |
| Activity volume | Meetings (with per-person and distinct counts, CRM 42), logged emails, calls and notes by person |

Salespeople see their own figures, direction managers their direction, executives all. **No margin or cost measure exists in CRM.**

## 10. Google Workspace activity

Unchanged from v2 (CRM 11, 55–61): calendar meetings with CRM contacts are logged automatically (admin-connected, 24 months of history, metadata only, private and internal-only events excluded). Emails are logged on demand with the full body. There is no write-back except the optional task due-date push. An unassigned meeting on an account with several open deals appears in the Owner's Morning Brief as "assign to deal".

## 11. Handover on Won

On Won, the salesperson enters the **contract signing date**, identifies the accepted proposal revision and its terms in Commercial (including the advance percentage and the recurring terms Billing needs), and chooses the **delivery type** (Simple purchase, Installation or Development; default Installation). The system creates exactly one project from the template for that direction and delivery type, with the direction's default PM or, while none is named, the deal Owner flagged to the direction manager (PM 25). The PM then splits the project into delivery batches. Retries never create a second project. The one-off amount and each recurring line carry into Commercial with their types and currencies. A related deal that is still open or Lost gets no project.

## 12. Permissions

The launch roles in Access_and_Permissions_v3.3.md apply:

| Role | CRM rule |
|---|---|
| Salesperson | Sees all opportunities and values in their own direction; edits their own; maintains contacts of accessible customers; creates opportunities, including Renewal tenders (CRM 83) |
| Direction manager | Everything in their direction: reassigns Owners, reverts Won, configures the pipeline and the contact-coverage threshold (CRM 66), merges duplicates, sets targets, edits shared identity fields, views the briefs of people in their direction (CRM 98) |
| Executive | Views all directions; sets targets for anyone; views anyone's brief (CRM 98) |
| Admin | Users, roles and settings; offboarding (CRM 78). No automatic view of deal values. |

The same scope applies to boards, search, the Morning Brief, notifications, exports, dashboards and prepared emails. Hidden records are left out of totals, never counted as zero.

## 12a. Notifications and tasks

| Notification | Recipient | Timing |
|---|---|---|
| Morning Brief sections (CRM 73) | Each user | Always current; the home screen |
| Deal reassigned | New Owner | Instant |
| Deal Won or Lost | Direction manager | Instant |
| Upsell lead raised from Billing | Owner | Instant |
| Renewal tender created (CRM 83) | Owner, account owner, direction manager | 6 months before the coverage ends |
| Weekly summary: pipeline changes, flagged deals | Direction manager | Weekly |

**Tasks** (CRM 51): a task can be assigned to any user. Only the Owner's task can be the designated next action. Assignees who cannot otherwise see the deal see the task and deal name only.

## 13. Cross-module impacts (current documents, 28 September 2026)

| Module | Alignment |
|---|---|
| PM | Delivery type chosen at Won; templates per direction × delivery type; default PM per direction |
| Billing | Upsell leads land as Lead-stage opportunities (§5). Renewals stay in Billing, except Renewal tenders (CRM 82–83). The signing date starts the advance (CRM 81). |
| Access | Launch roles; Admin gains no financial view; offboarding is an Admin action |
| Shared Data / migration | Monday stages map to the shared pipeline (§14). The Owner of an imported open deal must be a real user. Imported Won deals need no signing date. |
| Commercial | Captures the advance percentage and the recurring terms per joining rule at acceptance, and records amendments after Won (Commercial v3.2) |
| Project Context | Directions renamed; Lead as a stage; Morning Brief; first-release exclusions |

## 14. Migration notes

CRM 50 and Monday_Migration_Mapping_v1.md stand, with one change: imported stages map to the **shared pipeline** (CRM 65) rather than the v2 per-direction pipelines. The stage-mapping table in the migration mapping must be updated before the final delta. Imported leads that were never deals are not imported. Directions labelled CMS or Voix in any source map to Digital Signage and VOIX + CF.

## 15. Functional review scenarios

1. A salesperson creates a Lead-stage opportunity; they become Owner and a next action is required.
2. A second open deal for the same account and direction triggers a warning, not a block.
3. A stage change without a next action is refused. Completing the next action without a replacement flags the deal.
4. An overdue next action is flagged and appears in the Owner's Morning Brief. No fixed idle-day rule flags a deal.
5. A probability override is logged and resets on the next stage change; the weighted forecast uses it meanwhile.
6. A Digital ID / Security deal shows PoC/Pilot and Tender/Procurement; a Digital Signage deal shows neither.
7. A Lead-stage deal moves to Nurture with a revisit date and returns to the brief on that date.
8. An opportunity with a USD one-off amount, a EUR SaaS line and a GEL SLA line shows three separate values, per-type MRR and a GEL consolidation.
9. After 90 days with only notes, the system suggests Cold.
10. Lost requires a listed reason; *Not qualified* is available.
11. Only a direction manager reverts Won; the project is flagged, not deleted.
12. A Morning Brief never shows more than 10 items, and each section shows its full count.
13. Offboarding a salesperson moves their open deals, account ownership and tasks to the named successor, and history keeps the original name.
14. A salesperson in Digital ID / Security cannot find a Qmatic deal by search, export, brief, notification or dashboard total.
15. No CRM screen, export, dashboard or notification shows supplier costs, margins, invoices or payments.
16. A renewal of an existing SLA does not appear as a CRM opportunity.
17. Marking a deal Won without a signing date is refused. With a signing date and a 50% advance, Billing records the advance.
18. Six months before an HSM's prepaid maintenance ends, a Renewal tender opportunity appears in stage Qualified with the original one-year maintenance value, and the account owner and direction manager are alerted.
19. A Renewal tender marked Lost removes the expected renewal revenue from Billing's forecast.
20. Editing the one-off amount of a Won deal is refused, with a pointer to Commercial amendments; sales won still shows the sold value.
21. An open deal whose expected close month has passed shows "Expected close passed" on the board and in the Owner's brief, and is not counted as stale.
22. A deal above its direction's contact-coverage threshold with one customer contact is flagged "Contact coverage".
23. A task with a reminder date appears under Reminders in the assignee's brief on that date; a personal task is visible only to its owner.
24. Marking the brief as seen clears status changes only; tasks, flags and billing items stay.
25. A new opportunity opens with the next action "Qualify {account}: budget, timeline, decision maker", due in 5 days.
26. The author of a note edits it and the history shows the edit; a deleted call stays in the history as deleted; a salesperson can't edit a colleague's note.
27. Typing a company's ID number on a new opportunity finds the account; the opportunity can't change the account's ID number.
28. A customer with an active Qmatic Care contract and no D-ID deal shows Active for Qmatic and Prospect for Digital ID / Security, with a cross-sell hint for Digital ID. Its overall status shows Active.
29. A salesperson creates a Renewal tender manually for a public-sector Care renewal, linked to the original purchase; it follows the normal pipeline.
30. A deal with one customer contact and a 1,200,000 GEL one-off amount is flagged "Contact coverage"; one with 900,000 one-off and 900,000 recurring is not; one with no contact is flagged at any value.
31. A prepared billing-change email appears under "Emails to approve" in the brief of its recipients and designated approvers until it is sent or discarded.
32. A direction manager opens, read-only, the brief of a salesperson in their direction but not one outside it; an Admin without the Executive role cannot open anyone else's brief.

## 16. Open items

- The Renewal tender's first next action and its due date (CRM 83).
- The default PM per direction and direction-specific task lists (PM v3.3).
- The monday.com stage-mapping update (§14).
- **Deferred:** web forms and the lead inbox; custom stages and required fields per stage; international VOIX partner sales.

**Sources:** CRM_Module_v2.md (CRM 1–61); the review of the NGT CRM prototype (PROCESSES.md and ARCHITECTURE.md, 25 September 2026); change request CR-2026-09; decisions confirmed by the CEO on 25 September 2026; Billing_Module_v3.4.md (26 September 2026); the prototype gap review (NGT_CRM_Gap_Register, prototype commit 89d1d2a, 27 September 2026) and the CEO's confirmation of the adopted rules on 27 September 2026; the CEO's answers to the open questions of change request CR-2026-09 rev. 4 (28 September 2026).
