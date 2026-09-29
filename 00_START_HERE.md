# NGT integrated system — start here

**Starter pack for a new design conversation · 28 September 2026**
**From:** David (CEO, NGT Group)

Read this file first. It says what the project is, which attached documents are the source of truth, and how I'd like us to work.

## 1. What this is

NGT Group (Tbilisi; about 30 people; CX / Qmatic, digital identity and security, cash handling, digital signage, VOIX + CF, kiosks) is designing **one integrated internal system**: CRM, commercial records, project delivery and billing, with supplier costs to follow later. It will replace HubSpot and the relevant monday.com workflows.

The design is **functional**: the documents describe agreed rules, open questions and review scenarios, not built software. Production will be a fresh TypeScript build on PostgreSQL; hosting and data residency are still open.

A colleague, Luka Geldiashvili, built a working prototype that serves as the **test bench**. It is being aligned to these rules through a separate change request. **This conversation doesn't need that prototype or its repository.** Its visual style is captured in the UI style guide in this pack.

## 2. What to use this conversation for

- **Refining the design** module by module: resolving open items, adding detail, worked examples and review scenarios.
- **Light prototypes of specific areas** I want to improve, e.g. a batch-splitting screen, a billing calendar, the Morning Brief, a deal page. Each is one focused page, not a full app.
- Keeping the documents current whenever we decide something.

## 3. Attached documents: the source of truth

Current versions only. Where documents conflict, the newer decision wins; surface the conflict and ask.

| # | File | What it is |
|---|---|---|
| 1 | `NGT_Project_Context_and_Aims_v3.3.md` | **The shared brief.** Vision, modules, lifecycle, shared rules, boundaries, the working method (§12). Read it first. |
| 2 | `Solution_Architecture_v3.3.md` | Architecture decisions, module map, cross-module events, rollout and status |
| 3 | `CRM_Module_v3.3.md` | Opportunities, pipeline, next actions, value, forecasts, Morning Brief, targets |
| 4 | `Commercial_Module_v3.2.md` | Proposal revisions, accepted terms, advance, recurring terms, amendments |
| 5 | `PM_Module_v3.3.md` | Projects, templates, delivery batches, handover, cancellation review |
| 6 | `Billing_Module_v3.6.md` | The recurring engine, joining rules, batches and advances, renewals, handover; worked examples in §5 |
| 7 | `Access_and_Permissions_v3.3.md` | Six launch roles, default deny, the action matrix, surfaces, audit |
| 8 | `Shared_Data_and_Migration_v3.1.md` | Shared customer data, duplicates, migration from monday.com and accounting |
| 9 | `NGT_UI_Style_Guide_v1/` | The visual style and UI decisions for any prototype: the guide, `ngt-ui-tokens.css`, `ngt-starter.html` and 10 reference screenshots |

**Referenced in the documents, not in this pack.** I'll attach these if a topic needs them:
- `Costs_Module_v2.md`: supplier costs; deferred to a later release.
- `Monday_Migration_Mapping_v1`: the monday.com field and stage mapping; its stage table still needs updating for the shared pipeline.
- "Billing Scenarios – 3 Types of Care": the source sheet for the Care examples, which are already in Billing v3.6 §5.

## 4. How I'd like us to work

1. **Ask before assuming.** Ask focused questions, **one at a time**, mostly multiple choice, with your recommendation first. Don't reopen settled decisions without a concrete reason.
2. **Agree terms before rules.** I'm not an accountant. For billing topics, confirm the vocabulary (accrued vs billed vs paid, contract year, anniversary…) before discussing rules, and use worked numbers wherever money is involved.
3. **Keep confirmed, proposed and open apart.** Label proposals as *proposed*. Never present a recommendation as a decision.
4. **Flag cross-module impacts.** When a change in one module affects another, name the other document and the rule.
5. **Versioning.** When a module changes, produce a new version (e.g. CRM v3.4). It must have:
   - a "Changes from v3.3" table at the top;
   - a new refinement round with numbered decisions;
   - updated scenarios and open items.

   **Keep all still-valid content; don't condense it away.** Update the Context brief's document table when versions change.
6. **Rule numbers continue** from the current documents: CRM 99, Commercial 19, PM 26, Billing 67, Access 30, Arch 20, Data 15.
7. **Plain, short writing.** Short sentences and plain words, no jargon for its own sake. Use tables where readers compare items.
8. **Deliverables:** updated documents as files I can download, and prototypes as single-page HTML I can open or share.

## 5. Prototypes

- Use the **NGT UI Style Guide v1**: its tokens, components and the kept UI decisions (§6–§9), and **not** what its §10 lists.
- **Fictional data only**: invented customers, people and ID numbers.
- **One area per prototype**, small and fast to change. Show realistic states: flags, overdue items, empty and error states, and both light and dark themes.
- Follow the current rules. Use the worked examples (Billing §5, scenario lists) as test data, so the screen shows the right numbers.
- After a prototype session, list what the prototype taught us as **proposed changes** to the documents, and ask me before updating them.

## 6. Current state (28 September 2026)

- **Design documents:** v3.3 set. The 17 open questions from the latest review were answered on 28 September and are recorded in the documents.
- **Still open**, among others:
  - whether 1C, the accounting system, can export invoice and payment status;
  - approval limits for discounts, payment terms and advances;
  - default PMs and direction-specific task lists;
  - billing rules for directions other than CEM / Qmatic and D-ID;
  - Type 3 (large public) Care;
  - hosting, data residency and authentication;
  - who owns the shared GEL rate table.
- **Out of the first release:** supplier costs, invoice and payment tracking, the health score, the product catalogue and quotes, the lead inbox, service tickets, a rule engine, custom fields and a report builder.

## 7. Opening request

> Use the attached Project Context and Aims v3.3 as the shared context, the module documents as the detailed baseline, and the NGT UI Style Guide v1 for any prototype. Start by summarising, in a few lines, what you understand the system and its current state to be, and list the five most consequential open issues across the documents. Then ask me which area to work on first. Ask one question at a time, multiple choice with your recommendation.
