# NGT Group — Shared Data and Migration
**Functional draft 3.1 · 27 September 2026 · supersedes Shared_Data_and_Migration_v3.md**

**v3.1 adds the contract fields adopted in Billing v3.5** (contract number, term and notice period; Billing 61) to the billing import, and the one-off breakdown now uses HW / SW / PS (Commercial 13). Nothing else changes. The v3 introduction follows.

This revision aligns migration with CRM v3.1, PM v3.1, Commercial v3 and Billing v3.4 (26 September 2026). The main addition: what Billing needs from the old records to calculate correctly after go-live. That means:
- each recurring contract's settings and the inputs its joining rule needs;
- the state of the current contract year;
- open projects' delivery batches and advances.

CRM stages now map to the shared pipeline. Data 1–10 stand. No records have yet been imported into a live system.

## Changes from v3 (v3.1)

| Area | v3 | v3.1 | Ref |
|---|---|---|---|
| Recurring contract import | Settings, joining-rule inputs, auto-renew, currency | Also contract number, term and notice period where known | Data 11; Billing 61 |
| One-off breakdown | Categories from Commercial v3 | HW / SW / PS, as in every module | Commercial 13 |

## Changes from v2

| Area | v2 | v3 | Ref |
|---|---|---|---|
| CRM stage mapping | Per-direction pipelines | **Shared pipeline** (CRM 65); the stage table in Monday_Migration_Mapping_v1 must be updated | CRM v3 §14 |
| Billing inputs | "Active agreements, charge inputs, periods, prior handovers" | **Per recurring contract and line**: revenue type, joining rule, settings, auto-renew, plus the inputs each joining rule needs | Data 11 |
| Current contract year | Not specified | Renewal acceptance, annual quote, items already Done, supplementary charges | Data 12 |
| Open projects | Ongoing delivery and source links | Also **delivery batches** with allocations, official deliveries already made, and **advance received and offset so far** | Data 13 |
| Imported Won deals and prepaid terms | Won deals create no projects | Also need no signing date. Prepaid maintenance creates forecasts, and a Renewal tender at go-live if within 6 months of its end | Data 14 |
| Monday billing columns | Kept as legacy fields | Mapped: ARR/MRR → billing pattern; # of years → term or prepaid years; SLA units → units; grace months → remaining free months | §5 |

## 1. Confirmed decisions

| Ref | Decision | v3 status |
|---|---|---|
| Data 1 | Import active records and the history needed to support them. For CRM, all closed Won/Lost history is also imported. | Kept |
| Data 2 | Suggest duplicate customer/contact matches; a designated user confirms merges before import. | Kept (migration). Operational merges follow CRM 38. |
| Data 3 | Only direction managers edit shared customer details (legal name, tax ID/registration number, billing address). | Kept |
| Data 4 | Salespeople and account owners with access to the customer maintain its contacts. | Kept |
| Data 5 | Choose a primary source per data type and review conflicts manually. | Kept |
| Data 6 | Import incomplete records into a review queue; activate them only when essential fields are complete. | Kept; Billing essentials added in §6 |
| Data 7 | Copy attachments belonging to imported records. | Kept |
| Data 8 | Each module goes live for all its intended users together. | Kept |
| Data 9 | After cutover, the old workflow is read-only history. | Kept |
| Data 10 | Only the CEO confirms migration readiness before each module goes live. | Kept |

### Round D — alignment with Billing v3.4 (26 September 2026)

| Ref | Decision |
|---|---|
| Data 11 | **Recurring contracts are imported with their settings and joining-rule inputs.**<br>• **Per contract:** customer, direction, product line, revenue type, joining rule, accrual pattern, billing pattern, anniversary, auto-renew clause and currency, plus the contract number, term and notice period where known (Billing 61).<br>• **Per line:**<br>&nbsp;&nbsp;– Care: each sale's annual Care value and **official delivery date**. Without the date, the end of year 1 and the contract-year totals cannot be calculated.<br>&nbsp;&nbsp;– SLA: unit type, units, unit price, start month and remaining free months.<br>&nbsp;&nbsp;– SaaS: annual value or users × price, and the anniversary.<br>&nbsp;&nbsp;– Prepaid maintenance: annual value, years included and coverage end. |
| Data 12 | **The current contract year is imported as it stands.**<br>• Renewal acceptance: received, with its date and evidence, or pending.<br>• Whether the annual quote was sent.<br>• Which billed items have already been handed over.<br>• Any supplementary charges.<br>Handovers, acceptances and quotes are **never fabricated**. A missing fact stays missing and goes to the review queue. |
| Data 13 | **Open projects are imported with their delivery batches.**<br>• Each batch's allocation (one-off share, Care value, SLA units, SaaS value or users, prepaid years, free months).<br>• Batches already officially delivered, with their dates.<br>• The contract's advance: percentage, amount, and **how much has already been offset**, so the remaining batches are offset correctly.<br>Imported batch deliveries do not replay charges that were already handed over. |
| Data 14 | **Historical states never replay events.**<br>• Imported Won deals need no signing date (CRM 81) and create no projects.<br>• Imported prepaid maintenance creates its forecast from the coverage end. If the coverage ends within 6 months of go-live, a Renewal tender opportunity is created **at go-live** with an alert. It is not backdated. |

HubSpot and the relevant Monday.com workflows are replaced module by module. Monday boards outside the replaced workflows remain out of scope, including Testing Ground, Innovation Lab, New Workspace and Zeptos.

## 2. Migration scope

| Record family | Selection |
|---|---|
| Accounts | All accounts referenced by imported deals, plus those on the Monday customer boards, merged across boards |
| Contacts | None in Monday. Created from the Google Calendar backfill (CRM 58) and HubSpot if it holds any. |
| Opportunities | All Monday lead/deal items: open, Cold, Postponed, Won and Lost, mapped to the shared pipeline |
| Activities and tasks | Monday item updates become Notes; Monday task boards and reminder dates become Tasks |
| Commercial records | Accepted terms needed by active agreements and open projects, including one-off breakdowns, recurring terms (Commercial 12) and advance terms |
| Projects | Ongoing delivery, source links and **delivery batches** (Data 13); Monday Projects boards are mapped later |
| Billing | **Recurring contracts with settings and joining-rule inputs** (Data 11), the current contract year (Data 12), prior handovers and adjustments needed for correct future calculations; Monday recurring-payment boards are mapped later |
| Supplier costs | Deferred with the Costs module |
| Attachments | Files belonging to imported records, including acceptance evidence where it exists |

Excluding a record from import is never a deletion instruction. Retention and continued source access remain open.

## 3. Shared customer and contact stewardship

One shared customer identity, one account owner per direction, and no overall owner.

| Information or action | Authority |
|---|---|
| Legal name, tax ID/registration number, billing address | Direction managers (Data 3) |
| Other account fields: country, city, industry, customer/partner flag, website, parent account | *Proposed:* direction managers, with salespeople able to set industry and website |
| Contacts: name, title, email, phone, role in deal, active flag | Salespeople and account owners with access (Data 4) |
| Operational duplicate merges | Direction managers (CRM 38) |
| Cross-direction sharing | Admin (CEO or designated administrators) |
| Migration readiness | CEO only |

A change to shared identity never overwrites direction-specific owners, deals, contracts or activities. Customer creation, account-owner assignment and supplier-only identity editing remain open.

## 4. Duplicate matching and merging

**At migration (Data 2):**
1. Stage source records with their original IDs.
2. Propose matches.
3. A designated reviewer decides to merge, keep separate or defer.
4. Import the confirmed identity, keeping every source mapping.

Known cases from the first run:
- 137 inferred account matches (alias 146, exact 48, prefix 34 on deals).
- Ambiguous groups: Aversi Pharma vs Aversi Clinic branches, the Evex hospitals, and the Tegeta companies.
- Parent-account links (CRM 44) fit such groups.

**In operation (CRM 38):** the system warns about likely matches when a record is created and never blocks creation. Direction managers merge, keeping history. Merges never expose restricted financial records or communications through the merged customer.

## 5. Source precedence and provenance

| Data type | Primary source | Notes |
|---|---|---|
| Accounts | Monday customer boards, then deal names | Only 2 accounts have tax IDs; 106 accounts were created from deal names and flagged |
| Opportunities, state, stage, values | Monday lead/deal boards | Stages mapped to the **shared pipeline** (CRM 65); the mapping table must be updated |
| Recurring lines (CRM) | Monday Care, SaaS Annual and SLA Annual columns | Imported as 12-month amounts (MIG 4) |
| Recurring contracts (Billing) | Monday recurring-payment boards (mapping to follow) | **ARR/MRR** → billing pattern; **# of years** → term, or prepaid years for prepaid maintenance; **SLA units** → units; **grace months** → remaining free months |
| Official delivery dates | Accounting records of Revenue Service sign-offs | Needed for Care year 1 and SLA starts (Data 11); where missing, review queue |
| Advances | Accounting records | Amount invoiced and offset so far per open project (Data 13) |
| Notes and tasks | Monday updates, task boards and reminder dates | |
| Contacts | Google Calendar backfill, then HubSpot | HubSpot availability open |
| Meetings | Google Calendar (24 months) | Deduplicated by event ID |
| Emails | None imported | On-demand logging only (CRM 11) |

Provenance and flags are kept on every record; the first run produced 1,444 review flags. Missing values are never invented. Assumed values are flagged, such as "currency assumed" (MIG 3). Financial exceptions go to reviewers with the right financial scope.

## 6. Incomplete records and activation

Imported records missing essential fields stay in the review queue until complete (Data 6). For CRM, the clean-up week is this review period, before go-live.

**CRM:**

| Record | Essential to activate | Completed in clean-up week |
|---|---|---|
| Open, Cold or Postponed opportunity | Account, direction, owner (a real user, not "Former employee"), state, stage | Expected close date, next action, currency confirmation, stage flags |
| Postponed opportunity | Plus a return date | Checking the 21 generated return dates |
| Won or Lost opportunity | Account, direction, state, closed date (no signing date needed) | Lost reason (optional; defaults to "Not recorded (imported)") |
| Account | Name | Industry (about 110 missing), duplicate decisions |
| Contact | Name, email or phone, account | |

**Billing (new in v3):**

| Record | Essential to activate |
|---|---|
| Recurring contract | Customer, direction, product line, revenue type, joining rule, accrual and billing patterns, anniversary, currency |
| Care sale | Annual Care value, official delivery date |
| SLA line | Unit type, units, unit price, start month |
| SaaS line | Annual value or users × price |
| Prepaid maintenance | Annual value, years included, coverage end |
| Current contract year | Acceptance state (received or pending); quote sent (yes or no) |
| Open project | Delivery batches adding up to the contract totals; advance percentage and amount offset so far |

Won and Lost deals owned by departed staff keep "Former employee" as owner (MIG 5). Open deals go to the direction manager to reassign.

Old incomplete records never create new mandatory gates. Signed proposals and PM checklists remain optional. CEO readiness does not activate incomplete records by itself.

## 7. Attachments and activity history

Copy attachments of imported records with their filenames, parent links and a transfer check. Failed copies become exceptions. Access follows the target record's permissions.

**Google (CRM 55–61):** calendar history is backfilled 24 months at go-live, metadata only, private events excluded, deduplicated by event ID. Emails are not bulk-imported; future emails are logged on demand.

Monday updates imported as Notes do not reset the Cold clock (CRM 40).

## 8. Module-specific considerations

| Module | Detail |
|---|---|
| CRM | Mapping done (Monday_Migration_Mapping_v1.md); stage table to update for the shared pipeline. Historical Won deals create no projects and trigger no notifications; they need no signing date. Won values convert at their won-month GEL rate where available. |
| Commercial | Accepted terms and amendments, with one-off breakdowns, recurring terms (Commercial 12) and advance terms. Missing files never create signature requirements. |
| PM | Monday Projects boards mapped later. Open projects need delivery batches with allocations (Data 13). Never fabricate an official delivery. |
| Billing | Monday recurring-payment boards mapped later, using the column mapping in §5. Import settings and joining-rule inputs (Data 11) and the current contract year (Data 12). Do not replay events; preserve the meaning of Done. Imported prepaid maintenance forecasts from its coverage end (Data 14). |
| Costs | Deferred with the Costs module. |

Automations stay inactive until cutover checks pass.

## 9. Rollout and cutover

All intended users of a module start together (Data 8). The old workflow becomes read-only (Data 9), with no reverse mirroring. There is no limited-user pilot, though offline trial imports and training are proposed.

Cutover steps:
1. Define scope.
2. Prepare maps, deduplication and queues.
3. Rehearse and reconcile, including amounts by currency. For Billing, reconcile the next contract year's totals against the current recurring-payment boards.
4. Agree the final delta.
5. Present readiness evidence to the CEO.
6. Activate for all users and set the legacy workflow to read-only.
7. Verify.

For CRM, the rehearsal (the 25 September run) exists. The final delta must capture Monday changes made after it.

## 10. Readiness confirmation

Only the CEO confirms readiness (Data 10). Evidence:
- Scope and maps.
- Duplicate decisions.
- Record and amount reconciliation; for Billing, the next contract year per contract, and the remaining advance per open project.
- Open review-queue items.
- Currency and status mappings.
- Permission checks.
- Known exceptions.
- The cutover and recovery plan.

## 11. Functional review scenarios

1. All Monday deals, including closed history, import with source IDs, map to the shared pipeline, and create no projects.
2. Suggested account duplicates stay separate until the reviewer decides.
3. A salesperson updates contacts but not legal name or billing address.
4. Conflicts follow the source map, not "latest wins".
5. An open deal missing a close date or next action stays in the review queue until the clean-up week completes it.
6. Historical statuses do not replay automations.
7. A Care contract whose sales lack official delivery dates stays in the review queue.
8. An imported Type 1 Care contract with a February anniversary reproduces the next contract year's total from its sales and dates.
9. An open 100-branch project with two batches already delivered imports the remaining batches and the advance still to be offset; the delivered batches are not billed again.
10. An imported HSM whose maintenance ends in four months creates a Renewal tender at go-live, not backdated.
11. A current contract year with a pending acceptance imports as pending; no acceptance is invented.
12. The CEO confirms readiness before go-live, and retired Monday boards become read-only.
13. A direction manager edits shared identity without changing direction owners.
14. Attachments copy with their access mapped, and failures are listed.
15. Contacts created from the calendar backfill link to the right accounts through email-domain matching.
16. After go-live, a duplicate warning appears at account creation and a direction manager performs the merge.

## 12. Remaining detail

- Whether HubSpot holds contacts or email history.
- How many years of closed history to import (the first run imports 2024–2026).
- Mapping of the Monday Projects and recurring-payment boards, using §5.
- Where official delivery dates and advance offsets are held today (accounting records), and how complete they are.
- Merge reviewer appointment.
- Customer creation and account-owner assignment authority.
- Final-delta and recovery procedures.
- Legacy retention.
- The readiness-evidence format.

**Sources:** Shared_Data_and_Migration_v2.md; Monday_Migration_Mapping_v1.md (MIG 1–5 and the first run); CRM v3.1, PM v3.1, Commercial v3 and Billing v3.4; Commercial v3.1 and Billing v3.5 (27 September 2026). Items marked *proposed* are recommendations, not confirmed requirements.
