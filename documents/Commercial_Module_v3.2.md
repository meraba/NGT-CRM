# NGT Group — Commercial Management
**Functional draft 3.2 · 28 September 2026 · supersedes Commercial_Module_v3.1.md**

**v3.2 records one CEO decision** of 28 September 2026 (the open questions of change request CR-2026-09 rev. 4): **amendments are recorded by the deal Owner, the direction manager or the project's PM** (Commercial 18). The proposal in v3.1 had PMs only raising a request. Everything else in v3.1 stands. The v3.1 introduction follows.

**v3.1 adds two rules from the prototype gap review** (27 September 2026), confirmed by the CEO:
- A change to agreed quantities or prices after Won, including during delivery, is an **amendment**; PM then re-balances the delivery batches to the amended totals (Commercial 16).
- CRM locks a Won deal's amounts, so Commercial is the only place where agreed amounts change after Won (Commercial 17).

The one-off breakdown becomes **HW / SW / PS**, the same split as CRM (Commercial 13, revised).

The v3 introduction follows.

This revision aligns Commercial with Billing_Module_v3.4, CRM_Module_v3.1 and PM_Module_v3.1 (26 September 2026). Commercial now records what Billing needs to calculate charges:
- the **signing date** and the **advance**;
- the **recurring terms for each joining rule**;
- the **one-off breakdown** that PM uses to split delivery batches.

A won **Renewal tender** becomes a new purchase. The ten commercial decisions of v2 still stand; Commercial 4 is refined. It is a functional design, not implemented software.

## Changes from v3.1 (v3.2)

| Area | v3.1 | v3.2 | Ref |
|---|---|---|---|
| Who records an amendment | Proposed: the deal Owner or the direction manager; PMs raise the request | **The deal Owner, the direction manager or the project's PM** (a PM on assigned projects only) | Commercial 18; Access 25 |
| Renewal by tender | Automatic for prepaid terms | Also created manually by a salesperson for other tender-based renewals (CRM 83); a won one is still a new purchase | §8; Commercial 14 |

## Changes from v3 (v3.1)

| Area | v3 | v3.1 | Ref |
|---|---|---|---|
| One-off breakdown | Hardware, licences, services, development | **Hardware, software, professional services** (HW / SW / PS), as in CRM 69. Licences count as SW; installation, configuration and custom development count as PS. | Commercial 13 |
| Changes during delivery | An amendment "before delivery completes" | Every change to agreed quantities or prices after Won is an amendment with an effective date; PM re-balances the open batches; officially delivered batches are untouched | Commercial 16 |
| After Won | — | CRM amounts are read-only; Commercial records every later change | Commercial 17; CRM 85 |

## Changes from v2

| Area | v2 | v3 | Ref |
|---|---|---|---|
| Signing date | Not recorded | Recorded at Won, entered by the salesperson in CRM | Commercial 11, CRM 81 |
| Advance | Payment terms in general | **Advance percentage of 0–100%** of the one-off total plus year-1 Care; 10-day payment term by default | Commercial 11 |
| Recurring terms | "Price basis, frequency, term" per type; field sets open | **Field set per joining rule**: revenue type, product line, joining rule, amount basis, units, free months, prepaid years, auto-renew clause | Commercial 12 |
| One-off breakdown | Optional, categories open | **Hardware, licences, services, development**; used to split delivery batches | Commercial 13 |
| Renewal by tender | Not covered | A won Renewal tender is a **new purchase** linked to the original, not an amendment | Commercial 14 |
| Advance exceptions | — | *Proposed:* an advance below the segment's default is a payment-term exception | Commercial 15 |
| Supplier costs | Costs module | Costs module deferred to a later release | Architecture v3 |

## Changes from v1 (made in v2)

| Area | v1 | v2 | Source |
|---|---|---|---|
| Multi-direction sales | Opportunities grouped under a **sales initiative** | Opportunities linked as **related deals** with an optional group label; there is no initiative record | CRM 12 |
| Approval triggers | Discount, **margin** and payment-term exceptions | Discount and payment-term exceptions only | Costs 3–4, CRM 31 |
| Revenue categories | Configurable examples | **Fixed recurring types:** Care/Maintenance, SaaS, SLA | CRM 17, 21, 32 |
| Input from CRM | Summary lines per revenue type | One one-off amount plus recurring lines (Type, Name, 12-month amount, Currency) | CRM 21, 32 |
| Renewals and upsells | Boundary open | Renewals of the same recurring type stay in Billing. A new recurring type or new one-off scope is a new CRM Upsell opportunity. | CRM 19, 48 |
| Won reversal | Policy open | Only the direction manager reverts Won, with a reason; the project is flagged for cancellation review | CRM 30 |
| Currency | Open | GEL at monthly manual average rates; Won values frozen at the won-month rate | CRM 45 |

## 1. Decisions

| Ref | Decision | v3 status |
|---|---|---|
| Commercial 1 | Prepare proposals outside the app; attach them and record key prices and terms. In-app quote or document generation is not in scope. | Kept |
| Commercial 2 | Preserve every proposal revision with its own prices and terms, and identify the accepted revision. | Kept |
| Commercial 3 | Require internal approval only when configurable **discount or payment-term** limits are exceeded. | Kept; see Commercial 15 for advances |
| Commercial 4 | Salesperson confirmation is sufficient to mark an opportunity Won. Supporting documents are optional. | **Refined:** the contract **signing date** is required (CRM 81); the signed document stays optional |
| Commercial 5 | Support standalone purchases and purchases linked to an existing agreement. | Kept |
| Commercial 6 | Record changes through amendments with effective dates; require approval where commercial limits are exceeded. | Kept |
| Commercial 7 | Do not maintain a detailed product/service catalogue. | Kept (permanent boundary) |
| Commercial 8 | Enter summary lines by revenue type, with amounts, currencies and relevant terms. | Kept; recurring field sets in Commercial 12 |
| Commercial 9 | Marking an opportunity Won automatically creates a project from the relevant delivery template. | Kept |
| Commercial 10 | Create a separate project for each won opportunity, including related deals. | Kept |

### Round C — alignment with Billing v3.4 (26 September 2026)

| Ref | Decision |
|---|---|
| Commercial 11 | **Signing date and advance.** The accepted terms record:<br>• the **contract signing date**, entered by the salesperson to mark Won;<br>• the **advance percentage**, from 0% to 100% of the one-off total plus year-1 Care (whether other year-1 amounts, such as a SaaS first purchase, count is open in Billing);<br>• the advance payment term, 10 days by default.<br>Commercial customers are typically 50% or 100%; public institutions usually 0%. The advance invoice is issued outside the system. Billing records the advance and offsets it against batch invoices (Billing 49–51, 59). |
| Commercial 12 | **Recurring terms per line**, recorded at acceptance. The field set depends on the line's joining rule (Billing 52):<br>• **Every line:** revenue type (Care/Maintenance, SaaS, SLA), product line, joining rule, currency and auto-renew clause.<br>• **After year 1** (e.g. Qmatic Care): annual Care value per sale.<br>• **Units from delivery** (SLA): unit type (branch, user, custom module), units, unit price, free months.<br>• **Aligned to the anniversary** (SaaS, Mobile Token maintenance): a fixed annual value, or users × price per user per year.<br>• **Prepaid term** (e.g. HSM maintenance): annual maintenance value and years included.<br>The accrual, billing and anniversary settings default from the preset for that product and are confirmed in Billing. This closes the v2 open item on field sets per type. |
| Commercial 13 | **One-off breakdown** into hardware, software and professional services (HW / SW / PS), the same split as CRM 69. Licences count as software; installation, configuration and custom development count as professional services. It is optional but must add up to the one-off total. PM uses it to split delivery batches (PM 20). *Revised in v3.1; v3 had four categories.* |
| Commercial 14 | **Renewal tenders.** A won Renewal tender (CRM 82–83) is a **new purchase**, linked to the original one, with its own prepaid term. It is not an amendment. |
| Commercial 15 | *Proposed:* an advance below the default for the customer's segment counts as a **payment-term exception** and needs approval, for example 0% for a commercial customer. A public institution at 0% is its segment's default, not an exception. |

### Round D — prototype gap review (27 September 2026)

| Ref | Decision |
|---|---|
| Commercial 16 | **Changes after Won are amendments.** When agreed quantities or prices change after Won, including during delivery (for example an SLA going from 8 to 9 branches, or an extra hardware item), the change is recorded as an amendment to the purchase: the changed lines, the difference and an effective date. Approval applies as for any exception (Commercial 6).<br>On confirmation:<br>• the contract totals change;<br>• PM sees the new totals and re-balances the batches not yet officially delivered (PM 23);<br>• batches already officially delivered, and their charges, are untouched;<br>• Billing processes the change through its preview (Billing 5).<br>The CRM deal keeps the sold values (CRM 85). The project shows sold, amended, allocated and delivered side by side. A new recurring type or new one-off scope is still an Upsell (§8). *Adopted from the prototype's editable delivery scope, which let quantities change after the sale without changing the deal.* |
| Commercial 17 | **Only Commercial changes agreed amounts after Won.** CRM locks a Won deal's amounts (CRM 85). The accepted terms plus later amendments are the baseline for PM and Billing. |

### Round E — open questions answered (28 September 2026)

| Ref | Decision |
|---|---|
| Commercial 18 | **Who records an amendment.** The deal Owner, the direction manager of that direction, or the project's PM (on projects assigned to them) records an amendment (Commercial 16). The change usually surfaces during delivery, so the PM doesn't need to route it through the Owner. Approval still applies where commercial limits are exceeded (Commercial 6), and every amendment is audited (Access §5). |

Inventory, invoicing and payment management remain outside scope.

## 2. Purpose and boundary

Commercial management preserves what was offered, which version was accepted, any internal exceptions and later changes. Its structured values feed sales reporting, delivery planning (batches), the billing calendar and, in a later release, supplier-cost comparison.

The app records externally prepared proposals. It needs no proposal editor, document generator, SKU catalogue, price book or inventory.

A recorded agreement may have an attached contract, but a signed document is not a gate for Won; the signing date is. Keep the salesperson's confirmation, the signing date, internal approval state and document availability distinct.

**Commercial holds no supplier costs.** Approval rules use sales-side inputs only: amounts, discounts, payment terms and the advance.

Proposed workspaces: the opportunity's commercial tab, proposal history, agreement history, amendment history, and an approval inbox for assigned approvers.

## 3. Records and relationships

| Record | Purpose |
|---|---|
| Commercial purchase record | A confirmed purchase and its source opportunity; standalone, linked to an existing agreement, or a won Renewal tender linked to the original purchase |
| Proposal revision | A dated version of the offer, its optional file, structured amounts and terms |
| Revenue summary line | Revenue type, name, opportunity, amount, currency and the terms of Commercial 12 |
| One-off breakdown | Hardware, software, professional services (HW / SW / PS); adds up to the one-off total |
| Advance terms | Percentage, base, payment term, signing date |
| Agreement | A continuing commercial relationship that can support several purchases and amendments |
| Approval request and decision | The relevant revision, exception, approver, decision and timestamp |
| Sales confirmation | Who confirmed the purchase, when, the signing date and the selected terms |
| Amendment | Changes to agreed scope, quantities, amounts or terms: the changed lines and the difference, the effective date, who recorded it and relevant approvals (Commercial 16) |
| Project link | The project automatically created for the source won opportunity |

Keep purchase, agreement and proposal identities distinct. Later purchases under an agreement still have their own opportunities and projects.

**Related deals (CRM 12):** a proposal covering several directions can be stored once and referenced by each related opportunity (*proposed*). Its amounts are allocated to the opportunities, and each keeps its own win status, advance and project.

## 4. Structured commercial data

Fields for the purchase or revision:
- account, source opportunity, direction, revision date and status;
- summary lines with currencies, and the one-off breakdown;
- the advance terms and the signing date;
- the proposal reference or file where present;
- payment terms and delivery commitments.

| Type | Kind | Structured content |
|---|---|---|
| One-off | One-off | From CRM as a single amount and currency. Broken down into HW / SW / PS (Commercial 13). Split into delivery batches by PM. |
| Care/Maintenance | Recurring | Per Commercial 12: annual Care value per sale, or annual maintenance value and prepaid years |
| SaaS | Recurring | Per Commercial 12: fixed annual value or users × price; own service or vendor resale |
| SLA | Recurring | Per Commercial 12: unit type, units, unit price, free months |

**CRM gives a forecast; Commercial records the terms.** The CRM 12-month amount is a sales measure. At acceptance, the terms of Commercial 12 are recorded here so Billing can calculate billing and accruals. A 12-month amount alone cannot define a billing agreement.

**Currency:** each line keeps its original currency. Consolidated reporting uses GEL at the monthly manual rates; Won values are frozen at the won-month rate. Tax presentation remains open. Never infer taxes or combine unlike currencies.

## 5. Revision and acceptance workflow

1. Prepare the proposal externally.
2. Record a revision with its summary amounts, one-off breakdown, recurring terms and advance, and attach the document when available.
3. Evaluate the configured exception rules (discount, payment terms, advance below default).
4. Route exceptions for internal approval. Ordinary offers need no approval.
5. Preserve earlier revisions when the proposal or its terms change.
6. The salesperson identifies the accepted terms, enters the **signing date** and confirms Won.
7. The system creates the project from the relevant template, with the direction's default PM (or the deal Owner, flagged, while none is named; PM 25). Billing records the advance.

Record the selected terms at confirmation, so later edits to the CRM forecast cannot silently rewrite the delivery or billing baseline.

For a sale with no proposal file, the salesperson identifies the agreed structured terms. The record must not claim that a customer-signed document exists.

The app cannot technically block an externally sent proposal. The approval status must stay visible and tied to the right revision.

## 6. Exception approvals

Approval is conditional. The trigger categories are **discounts and payment terms** outside configurable limits, including an advance below the segment's default (*proposed*, Commercial 15). Margin is not a pre-sale trigger.

Rule inputs: direction, summary amounts, discount or reference amount where used, structured payment terms and the advance percentage. No thresholds or approvers are selected yet.

For each exception, keep the rule, input values, requested decision, assignee and decision history. A change to prices or terms does not inherit approval from a different revision.

Won confirmation and exception approval are distinct. Recording Won does not fabricate an approval; any unresolved exception is carried into the project's handover context. Whether execution must wait for approval remains a PM rule to decide.

## 7. Automatic project creation

**Each won opportunity creates its own project.** Related deals are linked for visibility; their delivery plans are not merged.

Creation behaviour:
- Choose the configured template for the opportunity's direction and delivery type.
- Create the project and link the customer, source opportunity, related deals, agreement or purchase, accepted revision, one-off breakdown and recurring terms.
- Seed template tasks and milestones, with source-relative dates where the template defines them.
- Include delivery commitments, files, recurring-service implications and outstanding commercial issues.
- Keep a traceable result, so retries reuse the existing opportunity–project link and never create a duplicate.

PM then splits the project into delivery batches (PM 20). Related deals won at different times each create their own project at their own win. A sibling that is still open, or Lost, gets no project.

**Won reversal (CRM 30):** only the direction manager can revert Won, with a reason. The accepted purchase record is kept and marked reverted; the project is flagged for cancellation review. Re-winning reuses the same opportunity–project link (*proposed*).

**Projects with no sale value** (PM 22) have no purchase record. They link to the customer's SLA contract.

## 8. Amendments, renewals and upsells

Amendments preserve the original baseline and record what changes and when. A later amendment must not silently overwrite an earlier billing calculation or project baseline.

| Change | Where it is handled |
|---|---|
| Renewal of an existing recurring contract, including quantity changes | Billing (acceptance and annual quote for Care; acceptance unless auto-renew for SLA and SaaS). No CRM opportunity. |
| Negotiated price indexation | An amendment here, applied in Billing through a preview (Billing 39) |
| Renewal by tender (e.g. HSM prepaid maintenance, or another tender-based renewal) | A **Renewal tender** opportunity in CRM (created automatically for prepaid terms, or manually by a salesperson for other tender-based renewals, CRM 83); when won, a **new purchase** (Commercial 14) |
| Correction or change to agreed quantities or prices of the same purchase, before or during delivery | Amendment to that purchase (Commercial 16); PM re-balances the batches not yet officially delivered |
| New recurring type or new one-off scope for an existing customer | New CRM Upsell opportunity, and a new project when won |

Commercial effective dates, PM Delivered dates and official delivery dates stay separate. Billing processes effective changes through its own preview-and-confirm rules.

## 9. Example flow

A customer makes one combined purchase from Direction A and Direction B:
- CRM has two opportunities linked as related deals, each carrying only its own one-off amount and recurring lines.
- A shared proposal file is referenced by both; each keeps its allocated summary lines and its own advance.
- Direction A is confirmed Won with its signing date, and Project A is created.
- Direction B is confirmed Won later, and Project B is created separately.
- Management reviews the related deals and both projects together, while plans, PMs, batches and acceptance stay distinct.
- If both belong to a continuing agreement, each links to it without being merged.

This is an illustrative design case, not a real transaction.

## 10. Functional review scenarios

1. An externally prepared proposal keeps all revisions and their structured values.
2. A normal offer needs no approval; a discount or payment-term exception has a traceable approval request.
3. Won cannot be recorded without a signing date; a signed attachment is still optional.
4. A 50% advance on a 500,000 one-off plus 30,000 year-1 Care is recorded as 265,000, with a 10-day term.
5. A public-institution purchase records a 0% advance without an exception.
6. A Care line records its annual Care value; an SLA line records unit type, units, unit price and free months; an HSM line records the annual maintenance value and years included.
7. The one-off breakdown adds up to the one-off total and is available to PM for batches.
8. A won Renewal tender creates a new purchase linked to the original.
9. Two won related deals produce two separate projects, with no duplicated revenue or scope.
10. No commercial action implies invoicing, payment or stock movement, and no Commercial screen shows supplier costs.
11. Reprocessing the same win does not create another project.
12. An amendment records an effective date and preserves the earlier agreement and calculation history.
13. An unresolved exception stays visible rather than being treated as approved by Won.
14. A same-type SLA renewal is handled in Billing; adding SaaS for an existing SLA customer starts a CRM Upsell.
15. A reverted Won keeps its purchase record, marked reverted, and flags the project for cancellation review.
16. An SLA sold for 8 branches is delivered for 9: an amendment records the extra branch from its effective month; PM's unallocated remainder shows it; the CRM deal still shows 8.
17. Editing the value of a Won deal in CRM is refused and points to a Commercial amendment.
18. The PM of a project records an amendment adding one SLA branch; a PM of another project cannot.

## 11. Remaining decisions

- Approval limits and approvers, including whether Commercial 15 is adopted.
- Default advance percentage per customer segment and direction.
- Tax and discount definitions.
- Allocation of shared proposals across related deals.
- Re-win behaviour after a reversal.

**Sources:** Commercial_Module_v2.md; Billing_Module_v3.4.md; CRM_Module_v3.1.md; PM_Module_v3.1.md; CEO decisions of 26 September 2026; the prototype gap review and CEO confirmation of 27 September 2026; the CEO's answers to the open questions of change request CR-2026-09 rev. 4 (28 September 2026). Items marked *proposed* are recommendations, not confirmed requirements.
