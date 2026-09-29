# NGT Group — Access and Permissions
**Functional draft 4.3 (v3.3) · 28 September 2026 · supersedes Access_and_Permissions_v3.2.md**

**v3.3 records the CEO's answers** to the open questions of change request CR-2026-09 rev. 4 (28 September 2026):
- **Access 24 is adopted:** direction managers and Executives can view other people's briefs.
- **Access 25 is decided with a change:** the project's PM can also record amendments.
- **Cross-direction sharing** shows the record, not its values (Access 26).
- **Admin names the outbox approvers** (Access 27).
- **Escalations** of items not handed over go to the Executives (Access 28).
- **Direction managers** set the contact-coverage threshold, and **salespeople** can create Renewal tenders manually (Access 29).

The roles and principles are unchanged. The v3.2 introduction follows.

**v3.2 adds the rights created by the prototype gap review** (27 September 2026): editing logged activities, the audit-log viewer, scoped search, the handover document and the outbox. It also proposes who may view other people's Morning Briefs and who records amendments. The roles and principles are unchanged. The v3.1 introduction follows.

**v3.1 adds the actions created by Billing_Module_v3.4, CRM v3.1 and PM v3.1** (26 September 2026):
- official delivery dates, renewal acceptance, annual quotes, contract settings and advance offsets;
- delivery batches and projects with no sale value;
- the signing date for Won, and Renewal tender opportunities.

The roles and principles of v3 are unchanged. The v3 introduction follows.

v3 applied the decisions agreed in the review of the NGT CRM prototype (25 September 2026). It defines **six launch roles**, separates roles from job titles, and makes "granular first, loosen when required" the governing principle. The delivery-staff role and all supplier-cost rights are deferred to later releases. The field-protection design is kept, so costs can be added later without restructuring.

No permissions have been applied to live systems. Where this document disagrees with Access_and_Permissions_v2.md, this document takes precedence.

## Changes from v3.2 (v3.3)

| Area | v3.2 | v3.3 | Ref |
|---|---|---|---|
| Other people's briefs | Proposed | **Adopted:** direction managers for people in their directions, Executives for anyone; Admin alone cannot | Access 24 |
| Amendments | Proposed: deal Owner or direction manager | **Deal Owner, direction manager, or the project's PM** (assigned projects) | Access 25 |
| Cross-direction sharing | Granted by Admin | Shows the record, its contacts and activity, **not values, prices or terms** beyond the recipient's own role | Access 26 |
| Outbox approvers | "Designated approvers" | **An Admin names them per email type**; changes audited | Access 27 |
| Escalation of items not handed over | — | To the **Executives** after 5 working days | Access 28 |
| Contact-coverage threshold; manual Renewal tenders | — | Direction managers set the threshold; salespeople create Renewal tenders manually in their directions | Access 29 |

## Changes from v3.1 (v3.2)

| Area | v3.1 | v3.2 | Ref |
|---|---|---|---|
| Logged activities | No rule | The author edits or deletes their own; direction managers in their directions; deletions keep a trace | Access 21 |
| Audit log | Recorded | Viewer: Executives see all entries; Admin sees user, grant, scope and settings entries only | Access 22 |
| Search | Covered by §4 | Global search named as a scoped surface | Access 23 |
| Other people's briefs | — | *Proposed:* direction managers for their directions, Executives for all | Access 24 |
| Amendments | — | *Proposed:* the deal Owner or the direction manager records them | Access 25 |
| Billing / Accountant | Official delivery, acceptance, quotes, settings, offsets | Also attaches the handover document; outbox recipients review and send | Access 18 (refined) |

## Changes from v3 (v3.1)

| Area | v3 | v3.1 | Ref |
|---|---|---|---|
| Billing / Accountant actions | Confirm official delivery, manage schedules, Done, adjustments, renewals | Adds: enter the official delivery date; SLA start in the following month; record renewal acceptance; send annual quotes; contract settings; advance offset overrides | Access 18 |
| Accrual schedules | — | Visible to Billing / Accountant, direction managers and executives only | Access 18 |
| PM actions | Manage scopes | Define **delivery batches** and their allocations; create **projects with no sale value** (with direction managers) | Access 19 |
| CRM and decisions | — | Signing date to mark Won; Renewal tenders in normal direction scope; direction manager decides when acceptance is missing | Access 20 |

## Changes from v2

| Area | v2 | v3 | Ref |
|---|---|---|---|
| Roles | Seven role families, including developer/installer/support and system administrator | **Six launch roles:** Salesperson, PM / Ops, Billing / Accountant, Direction manager, Executive, Admin | Access 11 |
| Role assignment | Not specified | **Explicit role grants with direction scopes**, separate from the free-text job title | Access 12 |
| Principle | Implied | **Default deny.** Start granular and loosen by explicit grant. | Access 13 |
| Delivery staff | Operational-only role (Access 8) | **Task-only access** at launch; the full role is deferred | Access 14 |
| Supplier costs | Direction managers maintain costs; figure-free overrun notices | **Deferred** with the Costs module | Access 15 |
| New actions | — | Offboarding, targets, optional-stage configuration, send to accountant / take back | Access 16–17 |

## 1. Decision record

| Ref | Decision | v3 status |
|---|---|---|
| Access 1 | Salespeople see sales values on all opportunities in their direction; never costs or margins | Kept |
| Access 2 | PM/Ops see sales values on assigned projects only | Kept |
| Access 3 | Direction managers maintain supplier costs | **Deferred** (Access 15) |
| Access 4 | Figure-free overrun notices to PM/Ops | **Deferred** (Access 15) |
| Access 5 | Central billing sees prices, terms and schedules, without costs or margins | Kept; merged into Billing / Accountant (Access 11) |
| Access 6 | Direction managers view everything in their direction | Kept |
| Access 7 | Only the CEO or system administrators grant cross-direction sharing | Kept (Admin role); refined by Access 26: a share shows the record, not its values |
| Access 8 | Delivery staff see operational information only | **Narrowed** to task-only access (Access 14) |
| Access 9 | CEO and authorized executives view everything | Kept (Executive role) |
| Access 10 | Multiple roles combine, each with its own scope | Kept |

### Round F — prototype review (25 September 2026)

| Ref | Decision |
|---|---|
| Access 11 | **Six launch roles:** Salesperson, PM / Ops, Billing / Accountant (the central billing team and accountants together), Direction manager, Executive and Admin. Further roles are added only by explicit decision. |
| Access 12 | Each user has a **job title** (free text, display only) and one or more **role grants**, each with the directions it applies to where relevant. A job title never grants access. |
| Access 13 | **Default deny.** A user sees and does only what a grant allows. When a need appears, a grant is widened explicitly and logged, rather than starting broad. |
| Access 14 | A user with **no role** can sign in and see only the tasks assigned to them, with the name of the linked deal, project or account. They see no values, other activities or attachments. This covers delivery staff until their role is designed. |
| Access 15 | **Supplier-cost rights are deferred** with the Costs module. The cost and margin columns below are kept as a design reserve, and no screen shows them in the first release. |
| Access 16 | **Admins** manage users, role grants and scopes, settings and offboarding (CRM 78). Admin alone gives no view of deal values, prices or schedules. The CEO holds Executive and Admin. |
| Access 17 | **Direction managers** set targets for their direction; **Executives** set them for anyone (CRM 72). Direction managers configure their direction's optional stages, probabilities, lost reasons and Cold threshold (CRM 66). |

### Round G — alignment with Billing v3.4 (26 September 2026)

| Ref | Decision |
|---|---|
| Access 18 | The **Billing / Accountant** role also:<br>• enters the **official delivery date** (Revenue Service sign-off) and may set an SLA start to the following month, with a reason;<br>• records **renewal acceptance** and prepares and sends **annual quotes**;<br>• sets a recurring contract's accrual, billing and anniversary settings (previewed; applied from the next contract year);<br>• **overrides a batch's advance offset**;<br>• confirms supplementary Care charges.<br>**Accrual schedules** are visible only to Billing / Accountant, direction managers and executives. Billing administrators maintain the presets and joining rules. |
| Access 19 | **PM / Ops** define delivery batches and their allocations on assigned projects. *Proposed:* the PM or the direction manager of that direction creates **projects with no sale value** (PM 22). |
| Access 20 | **Salespeople** enter the contract signing date to mark their deals Won (CRM 81). **Renewal tender** opportunities follow normal direction scope; their alerts go to the account owner and the direction manager (CRM 83). *Proposed:* when renewal acceptance is missing, the **direction manager** decides case by case (Billing 28). |

### Round H — prototype gap review (27 September 2026)

| Ref | Decision |
|---|---|
| Access 21 | **Logged activities.** The person who logged a note, email, call or meeting can edit or delete it; direction managers can in their directions. A deletion keeps a trace in history and in the audit log. The stage log is never editable. Admin alone gives no right (CRM 92). |
| Access 22 | **Audit-log viewer.** Executives see the whole audit log. Admin sees entries about users, role grants, scopes and settings, without amounts. Any entry that carries values follows the value rules in §2. |
| Access 23 | **Global search** (CRM 93) is a surface like any other: results never include records outside the searcher's scope. |
| Access 24 | **Other people's Morning Briefs** (*adopted 28 September 2026*). A direction manager can view, read-only, the briefs of people whose grants are in their directions; Executives can view anyone's. Admin alone cannot. Only the person marks their own brief as seen (CRM 89). A viewed brief shows only what the viewer's own grants allow (CRM 98). |
| Access 25 | **Amendments** (Commercial 16, 18) are recorded by the deal Owner, the direction manager, or the project's PM on projects assigned to them; exceptions go to approval (Commercial 6). *Decided 28 September 2026; the proposal had PMs only raising the request.* |
| Access 18 (refined) | Billing / Accountant also attaches the handover document at official delivery (Billing 60). The recipients and designated approvers of an outbox email review, send and mark it (Billing 62). |

### Round I — open questions answered (28 September 2026)

| Ref | Decision |
|---|---|
| Access 26 | **Cross-direction sharing shows the record, not its values.** A sharing grant (Access 7) lets the recipient see the shared record, its contacts and its activity. Values, prices, terms and schedules stay hidden unless the recipient's own role grants already show them. |
| Access 27 | **Outbox approvers.** An Admin names the designated approvers for each type of prepared email in Settings (Billing 65). The recipients of an email can always approve it. Changes to approver lists are audited. |
| Access 28 | **Escalations.** Due billing items not handed over after 5 working days (configurable) appear in the **Executives'** brief (Billing 64). Executives see them with their values, as they see everything. |
| Access 24 (adopted) | Viewing other people's Morning Briefs, as worded in round H, is adopted. |
| Access 25 (decided) | Amendments are recorded by the deal Owner, the direction manager or the project's PM (see the round H row). |
| Access 29 | **Direction managers** set the contact-coverage threshold for their directions (CRM 87). **Salespeople** can create Renewal tender opportunities manually in their own directions (CRM 83). |

## 2. Launch role matrix

| Role | Record scope | Sales values | Prices, terms, schedules | Costs and margins *(later release)* |
|---|---|---|---|---|
| Salesperson | All CRM records in own directions; edits own deals | Visible | Hidden | Hidden |
| PM / Ops | Assigned projects | Visible on those projects | Hidden | Hidden |
| Billing / Accountant | Agreements, recurring contracts, schedules and accruals, batches awaiting official delivery, all directions | Accepted values in agreements only | Visible | Hidden |
| Direction manager | Everything in own directions | Visible | Visible | Visible |
| Executive | Everything, all directions (view) | Visible | Visible | Visible |
| Admin | Users, roles, settings | No automatic grant | No automatic grant | No automatic grant |
| No role (task-only) | Own assigned tasks | Hidden | Hidden | Hidden |

Role grants combine, each within its own scope (Access 10). A request succeeds only if one grant covers the action, the record and the field.

## 3. Actions

| Action | Authority |
|---|---|
| Create opportunities, including Renewal tenders; edit own; enter the signing date to mark Won | Salesperson (own directions) |
| Reassign Owner; revert Won; merge duplicates; edit shared identity fields | Direction manager (own directions) |
| Reopen a Lost deal | Its Owner, with a reason |
| Configure optional stages, probabilities, lost reasons, Cold threshold, contact-coverage threshold | Direction manager (own directions) |
| Set sales targets | Direction manager (own directions); Executive (all) |
| Maintain monthly GEL rates | Direction managers |
| Maintain industry list, email templates and other CRM lists | Admin |
| Assign tasks | Deal Owner, PM, direction manager; any user can be an assignee |
| Manage project tasks and delivery batches, including their allocations; mark Delivered; send to accountant / take back | PM / Ops on assigned projects |
| Create a project with no sale value | PM or direction manager of that direction (proposed) |
| Close project | PM |
| Enter the official delivery date; set an SLA start to the following month (with reason) | Billing / Accountant |
| Record renewal acceptance; prepare and send annual quotes | Billing / Accountant |
| Set a recurring contract's accrual, billing and anniversary settings; override a batch's advance offset | Billing / Accountant |
| Decide when renewal acceptance is missing | Direction manager (proposed) |
| See accrual schedules | Billing / Accountant, direction managers, executives |
| Manage schedules; confirm recalculations and overrides; mark Done; create adjustments; confirm renewals | Billing / Accountant |
| Maintain presets and joining rules (formula templates) | Billing / Accountant users designated as billing administrators |
| Raise an Upsell lead | Billing / Accountant |
| Edit or delete own logged activities | The author; direction managers in their directions (Access 21) |
| View the audit log | Executives (all entries); Admin (user, grant, scope and settings entries) (Access 22) |
| View another person's Morning Brief | Direction managers for people in their directions; Executives (Access 24) |
| Record an amendment | Deal Owner, direction manager, or PM on assigned projects (Access 25) |
| Attach the handover document at official delivery | Billing / Accountant |
| Review, send and mark an outbox email | Its recipients and designated approvers |
| Designate outbox approvers per email type | Admin (Access 27) |
| Receive escalations of billing items not handed over | Executives (Access 28) |
| Grant cross-direction sharing (record only, Access 26) | Admin (CEO or designated administrators) |
| Manage users, role grants, settings; offboard a user | Admin |
| Confirm migration readiness | CEO only |

Viewing rights never imply edit, delete or approval rights.

## 4. Surfaces

The same grants apply to screens, search, the Morning Brief, notifications, exports, dashboards, reports, prepared emails, attachments, APIs and integration payloads. Aggregates never include hidden records and never show them as zero. Logged email bodies and synced meetings follow the permissions of the record they are linked to.

## 5. Audit

Record every role grant and removal, scope change, sharing grant, offboarding, Won reversal, merge, pipeline configuration change, target change, rate change, override, adjustment and official-delivery date. Also record every signing date, renewal acceptance, annual quote sent, contract-settings change, advance-offset override, SLA start moved to the following month, missing-acceptance decision, and creation of a project with no sale value. Also record every edit or deletion of a logged activity, every amendment, every handover document attached, and every outbox email prepared, sent or discarded. Also record every change to outbox approver lists and to the contact-coverage threshold.

## 6. Enforcement

Enforcement belongs on the server: in database row-level policies and in server-side field and aggregate checks (Solution_Architecture_v3.3.md). The prototype's browser-side checks are acceptable for walkthroughs with test data only.

## 7. Functional review scenarios

1. A Digital ID / Security salesperson sees every deal in that direction and none in Qmatic, through any surface.
2. Changing someone's job title to "Accountant" grants nothing; only a Billing / Accountant grant does.
3. An Admin who is not an Executive cannot see deal values or schedules.
4. A task-only installer sees the site-survey task and the deal name, with no values.
5. A PM sees values on their own projects only.
6. The Billing / Accountant role confirms official delivery and cannot see the CRM pipeline.
7. A salesperson in two directions with manager rights in one gets manager actions only in that one.
8. A widened grant is logged with who granted it and when.
9. A salesperson cannot see a customer's accrual schedule; a direction manager for that direction can.
10. A PM defines batches on an assigned project but cannot enter the official delivery date.
11. Only the Billing / Accountant role records a renewal acceptance or marks an annual quote sent.
12. A Renewal tender in Digital ID / Security is visible to that direction's salespeople and hidden from others.
13. A salesperson edits a note they logged; they can't edit a colleague's note unless they manage that direction.
14. An Admin who is not an Executive opens the audit log and sees role-grant entries but no deal values.
15. Global search by a Digital ID / Security salesperson returns no Qmatic deal.
16. A direction manager opens, read-only, the brief of a salesperson in their direction, but not the brief of someone outside it.
17. An Admin who is not an Executive cannot open anyone else's brief.
18. The PM of a project records an amendment on it; a PM of another project cannot.
19. A Digital ID salesperson given a shared Qmatic deal sees the deal, its contacts and activity, but no values or prices.
20. Only the recipients of a billing-change email, and the approvers an Admin named for that email type, can send it.
21. A billing item left un-handed-over for 5 working days appears in each Executive's brief.

## 8. Remaining detail

- The production user-to-role mapping (the test-bench mapping is in CR-2026-09 rev. 4).
- Whether to split Billing / Accountant into two roles later.
- The full delivery-staff role.
- Cost rights when Costs returns.
- Audit retention.

**Sources:** Access_and_Permissions_v2.md and v3; the review of the NGT CRM prototype (25 September 2026); change request CR-2026-09; CRM v3.1, PM v3.1 and Billing v3.4; the prototype gap review (NGT_CRM_Gap_Register, 27 September 2026); CRM v3.2, Commercial v3.1, PM v3.2 and Billing v3.5; the CEO's answers to the open questions of change request CR-2026-09 rev. 4 (28 September 2026).
