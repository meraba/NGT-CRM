# NGT Group — Project Management
**Functional draft 7.3 (v3.3) · 28 September 2026 · supersedes PM_Module_v3.2.md**

**v3.3 records two CEO decisions** of 28 September 2026 (the open questions of change request CR-2026-09 rev. 4):
- The **PM records an amendment** on their own projects, instead of only raising it (PM 23, refined; Commercial 18).
- The **seed task lists in §2 apply to all six directions** until direction managers refine them. No default PMs are named yet, so the deal Owner becomes PM, flagged to the direction manager (PM 25).

Everything else in v3.2 stands. The v3.2 introduction follows.

**v3.2 adopts three rules from the prototype gap review** (27 September 2026), confirmed by the CEO:
- Quantity or price changes during delivery come through a Commercial amendment, and the PM re-balances the batches (PM 23). The project shows sold, amended, allocated and delivered side by side, as the prototype's "Sold vs Delivering now" view does.
- Notifications at each handover step (PM 24).
- The one-off share of a batch uses the HW / SW / PS split (PM 20, revised).

The v3.1 introduction follows.

**v3.1 aligns PM with Billing_Module_v3.4** (26 September 2026):
- **Delivery batches** replace the v3 "delivery scopes". Each batch carries its share of the one-off amount *and* of the recurring items, and is invoiced separately at its own official delivery.
- A **project with no sale value** can be created for launches without a sale.
- The accountant's **official delivery date** (the Revenue Service sign-off) replaces the suggested billing start.

The v3 introduction follows.

v3 applied the decisions agreed in the review of the NGT CRM prototype (25 September 2026). It **lightens PM for the first release**: templates become task checklists with target durations, while dependencies, delay rescheduling, effort estimates and workload views are deferred. It adopts the prototype's delivery flow per batch and its "send to accountant" handover. The supplier-cost links are deferred with the Costs module.

It is a functional design, not implemented software. Where it disagrees with PM_Module_v2.md, this document takes precedence.

## Changes from v3.2 (v3.3)

| Area | v3.2 | v3.3 | Ref |
|---|---|---|---|
| Amendments during delivery | The PM or the salesperson raises an amendment in Commercial | The PM records it on assigned projects; so can the deal Owner and the direction manager | PM 23 (refined); Commercial 18 |
| Templates and default PMs | Seed lists as a starting point; default PMs and direction-specific lists open | The seed lists apply to all six directions; default PMs not yet named, so the Owner fallback applies | PM 25 |
| Cross-references | CRM v3.1, Access v3.1 | Current documents | §2, §7 |

## Changes from v3.1 (v3.2)

| Area | v3.1 | v3.2 | Ref |
|---|---|---|---|
| Batch one-off split | Hardware, licences, services | HW / SW / PS, as in CRM 69 and Commercial 13 | PM 20 |
| Quantity or price changes during delivery | Not covered | Commercial amendment, then the PM re-balances open batches; sold / amended / allocated / delivered view | PM 23 |
| Notifications | Send to accountant notifies Billing | Also: PM on creation and reassignment; reminder while a Delivered batch isn't sent; accountants on take back | PM 24 |
| Official delivery evidence | — | The accountant can attach the Revenue Service handover document | PM 21 (refined); Billing 60 |
| Batch invoice wording | One-off share plus year-1 Care | One-off share plus year-1 recurring (Care, a SaaS first year, prepaid maintenance), as in Billing 45–57 | §4 |

## Changes from v3 (v3.1)

| Area | v3 | v3.1 | Ref |
|---|---|---|---|
| Unit of delivery and billing | Delivery scope with a share of the one-off amount | **Delivery batch** with shares of the one-off amount and of the recurring items (Care value, SLA units, SaaS value or users, prepaid maintenance years) plus free months; invoiced separately | PM 20 |
| Allocation check | — | Batches must add up to the contract totals; any unallocated amount is shown, with a warning before sending | PM 20 |
| Official delivery | Accountant confirms; system suggests a billing start | Accountant **enters the official delivery date** (Revenue Service sign-off); recurring starts follow Billing's joining rules | PM 21 |
| Launches without a sale | Not covered | **Project with no sale value**, linked to the customer's SLA contract | PM 22 |

## Changes from v2

| Area | v2 | v3 | Ref |
|---|---|---|---|
| Depth | Tasks and subtasks, milestones, dependencies, delay suggestions, PM effort estimates, workload | **Tasks, milestones and delivery batches.** Dependencies, delay suggestions, effort and workload are deferred. | PM 13 |
| Templates | Per direction and delivery type; list open | **Three seeded delivery types:** Simple purchase, Installation, Development. Each template is a task checklist with day offsets and a target duration. | PM 14 |
| Delivery type | How the sale identifies it was open | **Chosen by the salesperson at Won** (default Installation) | PM 15 |
| Target date | Not defined | Won date plus the template's target duration | PM 16 |
| Handover flow | Operational completion, then a future accounting page | **Per batch:** Working → Waiting on customer → Delivered → Sent to accountant → Official delivery confirmed | PM 17 |
| Interim accounting UI | Needed, not designed | Send to accountant / Take back, with confirmation in Billing | PM 17, Billing 15 |
| Daily view | Not defined | PM items in the Morning Brief | PM 18 |
| Costs at closure | Closure marks supplier costs complete | **Deferred** with the Costs module | PM 19 |

### Round G — alignment with Billing v3.4 (26 September 2026)

| Ref | Decision |
|---|---|
| PM 20 | **Delivery batches** (revises PM 17). A batch has a name, a planned month and:<br>• its share of the one-off amount, optionally split into HW / SW / PS (revised in v3.2);<br>• its share of the recurring items: Care value, SLA units per line, SaaS annual value or users, prepaid maintenance years;<br>• any **free months**.<br>Batches are set **manually** by the PM or whoever plans the delivery; easier ways to split will be designed later. The shares must add up to the contract totals: the unallocated remainder is always shown, and sending a batch while something is unallocated gives a warning. Hardware-first deliveries, partial deliveries and billing milestones are all batches; PM milestones remain planning markers. Each batch is invoiced separately at its official delivery, with its share of the advance offset (Billing 45–51). |
| PM 21 | **Official delivery date.** In Billing, the accountant enters the date the handover document was signed off on the Revenue Service portal (Billing 20). Recurring items start from that date by their joining rules (Billing 21, 34, 41–42, 57). For SLA units, the accountant may set the start to the following month, with a reason (Billing 34). The PM's Delivered never counts as official delivery. |
| PM 22 | **Projects with no sale value.** When NGT launches an additional branch where the customer already owns the licences and hardware, the PM or direction manager creates a project **without a Won opportunity**. It is linked to the customer and its SLA contract, and its batches carry SLA units and free months. Its official delivery changes the SLA (Billing 35). It follows the same flow as any other project. |

### Round H — prototype gap review (27 September 2026)

| Ref | Decision |
|---|---|
| PM 23 | **Changes during delivery.** When agreed quantities or prices change after Won (for example SLA 8 → 9 branches), the PM or the salesperson raises an amendment in Commercial (Commercial 16); the PM doesn't edit the contract totals. Once the amendment is confirmed, the unallocated remainder reflects the new totals and the PM re-balances the batches not yet officially delivered. Batches already officially delivered never change. The project shows each line as **sold, amended, allocated and delivered**, so the difference from the sale is visible without changing the CRM deal (CRM 85). *Adopted from the prototype's "Sold vs Delivering now" view.* |
| PM 24 | **Notifications.** The PM is notified when a project is created for them and when a project is reassigned to them. After a batch is marked Delivered, the PM is reminded to send it to the accountant until they do. The Billing / Accountant role is notified when a batch is sent and when it is taken back. |
| PM 21 (refined) | The accountant may attach the Revenue Service handover document when entering the official delivery date (Billing 60). The date stays mandatory; the document is optional. |

### Round I — open questions answered (28 September 2026)

| Ref | Decision |
|---|---|
| PM 23 (refined) | **The PM records the amendment.** When agreed quantities or prices change during delivery, the PM records the amendment in Commercial for a project assigned to them (Commercial 16, 18); the deal Owner and the direction manager can also record it. Nobody edits the contract totals directly: the amendment changes them, and the PM then re-balances the batches not yet officially delivered. |
| PM 25 | **Starting templates and PMs.** The seed task lists in §2 (Simple purchase, Installation, Development) apply to **all six directions** until each direction manager refines them. No default PMs are named yet, so each project's PM is the deal Owner, flagged to the direction manager (§2), until default PMs are set in Settings. |

## 1. Decision record

| Ref | Decision | v3 status |
|---|---|---|
| PM 1 | Assign the direction's default PM on creation; allow reassignment | Kept |
| PM 2 | Templates by direction and delivery type | Kept; refined by PM 14 |
| PM 3 | Show delay impact and suggest revised dependent dates | **Deferred** by PM 13 |
| PM 4 | PM records approximate effort; no time logging | Effort **deferred** by PM 13; no time logging stays |
| PM 5–7 | Native tasks now, Jira later; two-way sync; conflicts flagged | Kept (Jira later) |
| PM 8 | Partial handover by branch, milestone or batch | Kept; flow in PM 17, batches in PM 20 |
| PM 9 | PM confirmation completes operational handover; accountants confirm official delivery | Kept; interim UI in PM 17 |
| PM 10 | Agreement rules suggest billing start; accountants confirm | **Revised** by PM 21: the accountant enters the official delivery date, and starts follow Billing's joining rules |
| PM 11 | Team members self-assign native tasks; PMs override | Kept |
| PM 12 | PMs close projects once operational delivery is complete | Kept |

### Round F — prototype review (25 September 2026)

| Ref | Decision |
|---|---|
| PM 13 | **First-release depth:** tasks (owner, due date, status, notes), milestones and delivery batches. Dependencies, delay-impact suggestions, effort estimates and workload views are deferred. Their data relationships may be designed now but are not built. |
| PM 14 | **Templates** exist per direction × delivery type. Three delivery types are seeded: **Simple purchase**, **Installation** and **Development**. Each template is a checklist of tasks with an offset in days from Won and a default role, plus a target duration. The template version is recorded on the project. |
| PM 15 | The salesperson chooses the **delivery type at Won** (default Installation). A missing template for that combination falls back to the direction's Installation template and is flagged to the PM. |
| PM 16 | **Target date** = Won date + the template's target duration. The PM can change it; the change is logged. A project is **Overdue** when the target date has passed and not every batch is Delivered. |
| PM 17 | **Delivery batches** (called scopes in v3; extended by PM 20): the PM can split a project into batches (by branch, milestone or part of the delivery), each with a name, its share of the one-off amount and the recurring lines or quantities it covers. A project with no batches defined is one batch. Each batch moves **Working → Waiting on customer → Delivered** (PM, with delivery date) **→ Sent to accountant** (PM; *Take back* returns it to Delivered) **→ Official delivery confirmed** (accountant, in Billing). Confirming one batch never confirms the others. |
| PM 18 | The **Morning Brief** shows PMs their overdue projects, delivered batches not yet sent, projects in cancellation review and tasks due. Accountants see batches awaiting confirmation (Billing 15). |
| PM 19 | Links to supplier costs are **deferred with the Costs module**. Closure does not mark costs complete in the first release, and there are no overrun notices. |

## 2. Project creation and templates

On Won (CRM v3.3 §11, which requires the contract signing date) the system creates exactly one project, linked to the customer, the source opportunity, the direction, the accepted commercial terms, related deals and any continuing agreement. It applies the template for the direction and delivery type and assigns the direction's default PM, or the deal Owner if no default PM is set (flagged to the direction manager). The PM is notified (PM 24). Retries never create a second project. Imported historical Won deals create no projects. A project with no sale value is created manually (PM 22).

**Seed templates** (starting point; direction managers and PMs refine them):

| Delivery type | Example tasks (offset from Won) | Target |
|---|---|---|
| Simple purchase | Confirm order with supplier (2 days) · Receive goods (14) · Deliver and get acceptance (21) | 30 days |
| Installation | Kick-off with customer (3) · Order equipment (5) · Site readiness check (20) · Install and configure (35) · Training (40) · Acceptance (45) | 45 days |
| Development | Requirements sign-off (10) · Build (depends on scope) · Customer testing · Go-live · Acceptance | Set per project |

These lists apply to all six directions for now (PM 25). Still open: default PM names per direction, and direction-specific task lists.

## 3. Tasks

| Work type | Home |
|---|---|
| Project tasks | This app; seeded from the template, plus tasks the PM or team adds |
| CRM tasks for delivery staff (e.g. a site survey before Won) | CRM tasks (CRM 51); not project tasks |
| Development and installation tickets | Jira, once integrated (later) |

Team members self-assign tasks in projects they can access, and PMs can reassign (PM 11). A task needs no effort estimate. The meeting-notes parser (CRM 74) can also create project tasks.

## 4. Delivery flow and handover

```
Working ⇄ Waiting on customer → Delivered → Sent to accountant → Official delivery confirmed
                                     ↑______ Take back ______|
```

- **Delivered** records the delivery date. It is PM confirmation of operational completion for that batch (PM 9). No checklist, signature or file is mandatory.
- **Sent to accountant** records who and when, and notifies the Billing / Accountant role.
- **Take back** is allowed until confirmation and notifies the accountants.
- **Official delivery** happens in Billing. The accountant enters the official delivery date (Revenue Service sign-off). The accountant may attach the handover document (Billing 60). That creates the batch's invoice (its one-off share plus its year-1 recurring amounts, such as year-1 Care, a SaaS first year or prepaid maintenance, minus its advance offset) and adds its recurring items to the customer's contracts by their joining rules (Billing 20, 45–51).
- Batches must not double-count quantities, recurring lines or milestone amounts, and together they must add up to the contract totals (PM 20). After an amendment, they must add up to the amended totals (PM 23).
- Notifications and the send reminder follow PM 24.

The dedicated "To be Delivered Officially" accounting page remains a later addition. The Awaiting official delivery workspace in Billing is its interim form.

## 5. Closure

The PM may close the project once every batch is Delivered (PM 12). Items awaiting official delivery and billing work stay accessible and actionable after closure. Closure does not depend on Jira.

## 6. Won reversal and cancellation review

Unchanged from v2 §10a:
1. Only a direction manager reverts Won, with a reason.
2. The project gets a **Cancellation review** flag and banner; the PM and the direction manager are notified.
3. New task assignments pause; existing work stays visible.
4. Billing holds not-yet-Done items in Awaiting review; Done items are untouched.
5. The direction manager chooses **Cancel** (the project closes as Cancelled, history kept) or **Continue** (if the deal is re-won, the same project resumes).
6. Nothing is deleted.

## 7. Permissions

- The PM / Ops role sees assigned projects, including sales values, and manages tasks, batches and handover. It records amendments on assigned projects (PM 23, Commercial 18).
- Direction managers see every project in their direction; executives see all.
- The Billing / Accountant role confirms official delivery.
- PMs never mark billing items Done.
- Team members with task-only access see their assigned tasks and the project name, not values (Access v3.3).

## 8. Deferred to a later release

- Task dependencies, delay-impact suggestions and PM-confirmed rescheduling (PM 3).
- Effort estimates and workload views (PM 4).
- Two-way Jira synchronization (PM 5–7).
- The dedicated accounting page.
- Supplier-cost links, cost completion at closure and overrun notices (with the Costs module).

## 9. Functional review scenarios

1. A Won Installation deal in Kiosks creates one project with the Installation seed template, the default PM (or the deal Owner, flagged, while none is named; scenario 19) and a target 45 days after Won.
2. Re-saving the Won deal creates no second project.
3. A missing template falls back to Installation and is flagged.
4. A project with two batches has batch A officially confirmed while batch B is Working; only batch A's charges start.
5. A PM sends a batch to the accountant and takes it back; nothing activates.
6. A project past its target with an undelivered batch shows Overdue and appears in the PM's Morning Brief.
7. A reverted Won flags the project, pauses new assignments, holds future charges, and deletes nothing.
8. A team member self-assigns a task and the PM reassigns it.
9. A closed project still shows its batches awaiting official delivery.
10. PMs never see supplier costs or margins, and no cost features appear in the first release.
11. A 100-branch contract is split into a hardware batch, a licences-and-Care batch, and ten installation batches of 10 branches with 10 SLA units each. The shares add up to the contract totals, and the unallocated remainder shows 0.
12. Sending a batch while 15,000 of the one-off amount is unallocated gives a warning.
13. A branch launch without a sale is a project with no sale value; its official delivery adds 1 SLA unit after its free month.
14. The PM marking a batch Delivered creates no charges; only the accountant's official delivery date does.
15. An SLA sold for 8 branches is delivered for 9: an amendment is recorded in Commercial; the project shows sold 8, amended 9 and 1 unallocated until the PM adds it to a batch; the CRM deal still shows 8.
16. A batch already officially delivered keeps its allocation after an amendment; only open batches are re-balanced.
17. A PM is notified when a project is created for them, and reminded while a Delivered batch hasn't been sent to the accountant.
18. An SLA sold for 8 branches is delivered for 9: the PM records the amendment on the project; the unallocated remainder shows 1 branch until the PM adds it to an open batch.
19. A Kiosks project created with no default PM set gets the deal Owner as PM, and the Kiosks direction manager sees the flag.

## 10. Outstanding detail

- Default PMs per direction, and direction-specific task lists (the §2 seed lists apply meanwhile, PM 25).
- The Monday Projects board mapping.
- Reversal of an already-confirmed official delivery.
- Execution rules while a commercial exception is unresolved.
- A batch-splitting screen that is easy to use: splitting by branch count, by hardware / licences / services, or by copying the contract lines (PM 20).
- Who may create a project with no sale value (proposed: the PM or the direction manager of that direction).

**Sources:** PM_Module_v2.md; the review of the NGT CRM prototype (25 September 2026); change request CR-2026-09; CRM_Module_v3.1.md; Billing_Module_v3.4.md; the prototype gap review (NGT_CRM_Gap_Register, 27 September 2026); Commercial_Module_v3.1.md; the CEO's answers to the open questions of change request CR-2026-09 rev. 4 (28 September 2026).
