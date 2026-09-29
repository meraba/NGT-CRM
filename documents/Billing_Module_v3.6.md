# NGT Group — Billing Calendar and Rules
**Functional draft 11 (v3.6) · 28 September 2026 · supersedes Billing_Module_v3.5.md**

**v3.6 records the CEO's answers** to the open questions of change request CR-2026-09 rev. 4 (28 September 2026):
- **SLA and SaaS renewal acceptance** (contracts without auto-renew) is due by the contract's **cancel-by date**, with reminders 60 and 30 days before it (Billing 63).
- Due items not handed over **escalate to the Executives after 5 working days** (Billing 64).
- **Outbox approvers** are named per email type by an Admin (Billing 65).
- The accounting system is **1C**; whether it can export invoice and payment status is being checked (Billing 66).

The calculation rules and worked examples are unchanged since v3.4. The v3.5 introduction follows.

**v3.5 adds three rules from the prototype gap review** (27 September 2026), confirmed by the CEO, and fixes leftover wording:
- The accountant can attach the Revenue Service handover document to an official delivery (Billing 60).
- Each recurring contract records its contract number, term, notice period and cancel-by date (Billing 61).
- System-prepared emails go through the approval-gated outbox (Billing 62).
- A batch's one-off share uses the HW / SW / PS split. "Scopes" now read "batches", and the deposit and milestone triggers apply only to directions that don't have batch rules yet.

The calculation rules and worked examples are unchanged. The v3.4 introduction follows.

This revision covers **CEM / Qmatic** and **D-ID (Digital ID / Security)**, agreed with the CEO on 26 September 2026.
- v3.1 added Care and the billing vocabulary.
- v3.2 added SLA and SaaS on the **same recurring engine**. Every recurring contract has the same three settings (accrual, billing, anniversary); the types differ only in how a project enters the contract and how the amount is worked out.
- v3.3 added **delivery batches** and **advances**.
- v3.4 adds D-ID. It separates each recurring line's **revenue type** (for reporting) from its **joining rule** (for billing). It adds a fourth joining rule, **prepaid term with renewal by tender** (HSM maintenance), plus **per-user SaaS** and an **advance of 0–100% configurable per contract**.

Rules for other directions come next, direction by direction. Until then, the v3 templates for those stand as provisional.

It is a functional design, not implemented software. Where it disagrees with an earlier version, this document takes precedence.

## Changes from v3.5 (v3.6)

| Area | v3.5 | v3.6 | Ref |
|---|---|---|---|
| SLA and SaaS renewal deadline | Open; 60/30-day reminders provisional | Acceptance due by the contract's **cancel-by date**; reminders 60 and 30 days before it | Billing 63 |
| Escalation of items not handed over | After a configurable delay, recipient not named | After **5 working days** (configurable), to the **Executives** | Billing 64 |
| Outbox approvers | "A recipient or approver" | The email's recipients and the **approvers an Admin names per email type** | Billing 65 |
| Accounting system | Not named | **1C**; its export of invoice and payment status is being checked | Billing 66 |

## Changes from v3.4 (v3.5)

| Area | v3.4 | v3.5 | Ref |
|---|---|---|---|
| Official delivery | Date entered by the accountant | The Revenue Service handover document can be attached | Billing 60 |
| Recurring contract | Settings, anniversary, auto-renew | Adds contract number, term, notice period, cancel-by date and documents | Billing 61 |
| Emails | A person sends the annual quote | Every system-prepared email goes through the approval-gated outbox | Billing 62 |
| One-off split in batches | Hardware / licences / services | HW / SW / PS (CRM 69, Commercial 13) | §4, §5.4 |
| Wording | "Scopes" in §3 and §6; deposit and milestone triggers in §5.6 and §6 | "Batches"; deposit and milestone triggers limited to directions without batch rules | §3, §5.6, §6 |

## Changes from v3.3

| Area | v3.3 | v3.4 | Ref |
|---|---|---|---|
| Recurring lines | Type decides behaviour | **Revenue type** (Care/Maintenance, SaaS, SLA) is separate from the **joining rule** (after year 1 · units from delivery · aligned to anniversary · prepaid term) | Billing 52 |
| Contracts per customer | One per type | **One per product line**, each with its own anniversary | Billing 53 |
| SaaS amount | Annual value per project | Also **users × price**; users added mid-year are aligned to the anniversary | Billing 54 |
| D-ID own products | — | Mobile Token subscription and Mobile Token CAPEX + maintenance, both on the SaaS rule | Billing 55 |
| Devices without maintenance | — | One-off only | Billing 56 |
| HSM maintenance | — | **Prepaid term** billed and accrued with the CAPEX; renewal by tender, with a forecast, an alert and a CRM opportunity | Billing 57–58 |
| Advance | Usually 50% or 100% | **0–100%, configurable per contract**; public institutions usually 0% | Billing 59 |

## Changes from v3.2 (made in v3.3)

| Area | v3.2 | v3.3 | Ref |
|---|---|---|---|
| Project billing unit | One-off billed at official delivery; deposits and milestones as separate charge types | **Delivery batch**: each has its share of the one-off amount and the recurring items, its own official delivery and its own invoice. Hardware-first deliveries, partial deliveries and milestones are all batches. | Billing 45–48 |
| Recurring items in batches | Per project | **Per batch**, as if each batch were sold on its own date | Billing 47 |
| Advance | Deposit schedule from recorded terms | **Advance of 50% or 100%** of one-off plus year-1 Care. Invoiced at signing, due in 10 days. Accrued only at official delivery. | Billing 48–49 |
| Offset | Deposit and balance add up to the agreed amount | **Proportional offset** by default, overridable per batch; the offsets always add up to the advance | Billing 50–51 |
| Signing date | Not required | The **salesperson enters the signing date to mark Won** in CRM (cross-module impact) | Billing 49 |

## Changes from v3.1 (made in v3.2)

| Area | v3.1 | v3.2 | Ref |
|---|---|---|---|
| Recurring engine | Care settings only | **One engine for Care, SLA and SaaS**: the same three settings and the same rounding; each type has its own entry and amount rules | Billing 32 |
| SLA amount | Unit price × units (v3, provisional) | **SLA lines**: units × unit price; unit = branch, user or custom module | Billing 33 |
| SLA start | Following month (v3, provisional) | **Month of official delivery** by default; the following month case by case | Billing 34 |
| Launches without a sale | Not covered | A **PM project with no sale value**; its official delivery changes the SLA | Billing 35 |
| Free months | Handled by an override | **Free months per project**, for the units that project adds | Billing 36 |
| SLA contract and renewal | Provisional | Own anniversary; monthly by default; acceptance unless auto-renew; indexation negotiated | Billing 37–39 |
| SaaS (resold) | Monthly or annual (v3, provisional) | Configurable like Care; anniversary = first project's delivery month; later projects **aligned** to the anniversary; renewal as SLA | Billing 40–44 |

## Changes from v3 (made in v3.1)

| Area | v3 | v3.1 | Ref |
|---|---|---|---|
| Vocabulary | Loose use of charge, bill, invoice | **Accrued, billed, paid**, plus annual Care value, annual Care total, annual quote, renewal acceptance, contract year | Billing 19 |
| Official delivery | Accountant confirms delivery; system suggests a billing start | Accountant **enters the official delivery date**, bound to the Revenue Service portal sign-off | Billing 20 |
| Care year 1 | Covered from purchase; not billed by Care | **Full annual Care value billed and accrued in the official delivery month**, on the same invoice as the project one-off | Billing 21 |
| Care structure | One charge plan per recurring line | Each sale joins the customer's **CEM Care contract**, which has one anniversary | Billing 22 |
| Care amount | Annual amount plus prorated batches at the anniversary | **Annual Care total** per contract year, counting each sale only after its first year | Billing 23 |
| Care patterns | One annual pattern | Three settings: **accrual pattern, billing pattern, anniversary**. Type 1 and Type 2 are presets; Type 3 is parked. | Billing 24–25 |
| Rounding | 2 decimals per item | Same, and **the last month of a contract year takes the difference** | Billing 26 |
| Four-month rule | Care renewal invoice due 4 months ahead | **Renewal acceptance** due 4–3 months ahead, always required | Billing 27–28 |
| Annual quote | Not defined | Sent **1 month before** the anniversary | Billing 29 |
| Late deliveries | Not defined | **Supplementary Care charge**; the quoted total stays unchanged | Billing 30 |
| Accruals | Not shown | **Accrual schedule** shown next to billing on each Care contract (proposed) | Billing 31 |

## 1. Decision record

### Status of earlier decisions

| Ref | Decision | Current status |
|---|---|---|
| Billing 1–6, 8–9 | Central team; scope; Done; previews; adjustments; reminders; agreement currency | Kept |
| Billing 10 | Deposit and milestone schedules from recorded terms, triggered by dates or confirmed events | **Revised for CEM**: milestones are delivery batches (Billing 45) and deposits are advances (Billing 49–51) |
| Billing 7 | Auto-renew agreements continue; others need confirmation | Kept for CEM SLA and SaaS (Billing 38, 44). **Revised for CEM Care** by Billing 27: acceptance is always required. |
| Billing 11 | A predefined template per recurring type, overridable per agreement | Kept. CEM Care, SLA and SaaS are now presets on one engine (Billing 24–25, 32). |
| Billing 12 | Qmatic Care and vendor hardware maintenance are variants of one Care template | **Superseded for Qmatic Care** by Billing 21–26. Vendor hardware maintenance stays provisional. |
| Billing 13 | Billing changes view and notifications | Kept |
| Billing 14 | Care renewal states on the four-month rule; 60/30-day SaaS and SLA reminders | **Revised for CEM Care** by Billing 27: the states track renewal acceptance. CEM SLA and SaaS: Billing 38, 44; acceptance is due by the cancel-by date, with reminders 60 and 30 days before it (Billing 63). |
| Billing 15 | Send to accountant / take back / confirm official delivery; suggested billing start | Flow kept. **Revised** by Billing 20: the accountant enters the official delivery date. The start for each type follows Billing 21, 34 and 41–42. |
| Billing 16 | One charge plan per recurring line at official delivery | **Revised for CEM**: each project joins the customer's Care, SLA or SaaS contract under its entry rule (Billing 21–22, 34–36, 41–42) |
| Billing 17 | No invoice or payment tracking | Kept, and restated in the vocabulary of Billing 19 |
| Billing 18 | Dated schedule items; calendars are views over them | Kept. Recurring calendars gain an accrual row (Billing 31, 32). |

### Round G — CEM / Qmatic Care (26 September 2026)

| Ref | Decision |
|---|---|
| Billing 19 | **Vocabulary.** **Accrued**: the value of service booked as earned in a period. **Billed**: what NGT asks the customer to pay for a period; in this system, the charge the accountant hands over for invoicing. **Paid**: money received, recorded only in the accounting system. **Annual Care value**: the Care price agreed for one sale. **Annual Care total**: what a customer's Care contract comes to for one contract year. **Contract year**: 12 months starting at the anniversary. **Annual quote**: the annual Care total sent to the customer before the contract year. **Renewal acceptance**: the customer's explicit confirmation that Care continues. The Billing module manages *billed*, shows *accrued* (Billing 31) and never records *paid*. |
| Billing 20 | **Official delivery date.** The accountant enters it manually. It is the date the handover document was signed off on the Revenue Service portal. It drives year-1 Care and everything that counts from delivery. The PM's "Delivered" never counts as official delivery. |
| Billing 21 | **Year 1 for each sale.** The sale's full annual Care value is **billed and accrued in the month of official delivery**, on **one invoice** together with the project's one-off amount. Year 1 covers the delivery month and the next 11 months. |
| Billing 22 | **One CEM Care contract per customer.** Each sale's Care joins the customer's CEM/Qmatic Care contract, which has **one anniversary**. The anniversary defaults to the month of the first official delivery and is **configurable**. |
| Billing 23 | **Annual Care total.** For each contract year, sum each sale's annual Care value × (months of the contract year that fall after that sale's year 1) ÷ 12. A sale still in its first year for the whole contract year contributes nothing. |
| Billing 24 | **Three settings per Care contract**: accrual pattern (*monthly*, the total ÷ 12, or *annual* at the anniversary); billing pattern (*monthly* or *annual* at the anniversary); anniversary month. **All combinations are allowed**, including annual accrual with monthly billing, which is unused so far. |
| Billing 25 | **Presets.** **Type 1 · Standard customer**: monthly accrual; billing monthly or annual, chosen per contract. **Type 2 · Small customer**: annual accrual; annual billing. Both have a configurable anniversary. **Type 3 · Large public organisation** is parked: it has its own flow and will be defined later. More presets can be added without new logic. |
| Billing 26 | **Rounding.** Monthly amounts are rounded to 2 decimals. The last month of the contract year takes the difference, so the months add up exactly to the annual Care total. |
| Billing 27 | **Renewal acceptance is always required.** The customer must accept explicitly **4–3 months before the anniversary**. States: 5 or more months to go = *On track*; 4–3 months = *Acceptance due* (amber); 2–0 months without acceptance = *Overdue* (red). The acceptance is recorded with who, when and the evidence. |
| Billing 28 | **No acceptance.** If acceptance hasn't arrived, the next step is decided **case by case**: continue, pause or end Care. The decision and its reason are recorded. *Proposed:* the direction manager decides. |
| Billing 29 | **Annual quote.** Sent **1 month before the anniversary**, stating the annual Care total for the coming contract year. The system prepares it; a person sends it and marks it sent. |
| Billing 30 | **Late deliveries.** Sometimes an official delivery adds months to a contract year whose annual quote was already sent. This includes a delivery entered late with an earlier sign-off date. In that case the system creates a **supplementary Care charge** for those months, and the quoted total stays unchanged. *Proposed timing:* billed and accrued in the first month it covers. |
| Billing 31 | *Proposed:* each Care contract shows its **accrual schedule** next to its billing schedule, read-only, so accountants can book accruals from it. This is needed because Type 1 billed annually and Type 2 produce identical bills and differ only in accrual. |

### Round H — CEM / Qmatic SLA and SaaS (26 September 2026)

| Ref | Decision |
|---|---|
| Billing 32 | **One recurring engine.** Every recurring contract (Care, SLA, SaaS) has its own contract year and the three settings of Billing 24: accrual pattern, billing pattern and anniversary. The rounding rule (Billing 26) and the vocabulary (Billing 19) apply to all. Types differ only in **how a project enters** the contract and **how the amount is calculated**. The accrual schedule (Billing 31) is shown for every recurring contract. |
| Billing 33 | **SLA amount.** An SLA contract has one or more lines of units × unit price. The unit is a branch or a user, or, rarely, a custom module. Each line has its own price. Service levels, response times and visits are tracked in Jira, not here. |
| Billing 34 | **SLA start and quantity changes** take effect **in the month of official delivery**, as a whole month. The accountant can set a project to start the **following month** instead, case by case, with a reason. |
| Billing 35 | **Launches without a sale.** Sometimes NGT launches an additional branch where the customer already owns the licences and hardware. That launch is a **PM project with no sale value**, and its official delivery date triggers the SLA quantity change. Every SLA change therefore has an official delivery behind it. |
| Billing 36 | **Free months.** Any project, whether a new SLA or units added later, can include a number of free months for the units it adds. Free months are neither billed nor accrued. |
| Billing 37 | **SLA contract.** An SLA contract has its own anniversary and contract year, independent of Care. The default is monthly accrual and monthly billing. The settings are configurable; exceptions will be defined later. |
| Billing 38 | **SLA renewal.** An auto-renewing contract continues on the same terms. Otherwise the customer's **acceptance is required** before the next contract year, by the cancel-by date (Billing 63). |
| Billing 39 | **SLA price indexation** is negotiated case by case; the process will be defined later. An agreed new price is applied from a stated month through the change preview (Billing 5). |
| Billing 40 | **SaaS (resold).** Configurable like Care (Billing 24). The usual preset is **annual billing with monthly accrual**. |
| Billing 41 | **SaaS anniversary** is the month of the **first project's official delivery**; later projects follow it. The first project buys a full year from that month. |
| Billing 42 | **SaaS later projects are aligned to the anniversary.** A later project's first purchase covers the months from its official delivery month (included) up to the anniversary: its annual value × those months ÷ 12. It is billed and accrued according to the contract's settings. From the next anniversary it is part of the annual total. |
| Billing 43 | **SaaS annual total** for each contract year is the sum of the annual values of all projects in the contract. |
| Billing 44 | **SaaS renewal** follows SLA (Billing 38): acceptance is required unless the contract auto-renews. |

### Round I — CEM / Qmatic project charges (26 September 2026)

| Ref | Decision |
|---|---|
| Billing 45 | **The delivery batch is the unit of project billing.** Every project has one or more batches. Each batch has:<br>• its share of the one-off amount;<br>• its share of the recurring items: Care value, SLA units, SaaS annual value, free months;<br>• its own official delivery date (Revenue Service sign-off) and its own invoice.<br>Partial deliveries (for example all hardware now, licences and Care in three months, installation branch by branch over a year), multi-branch rollouts and milestones are all batches. A project with one delivery has one batch. |
| Billing 46 | **Batches are set manually** by the PM or whoever plans the delivery. The shares must add up to the contract totals. The system shows any unallocated amount and warns before an official delivery while something remains unallocated. Easier ways to split will be designed later. |
| Billing 47 | **Recurring items per batch** behave as if that batch were a separate sale on its own official delivery date. Care follows Billing 21–23, SLA follows Billing 34–36 and SaaS follows Billing 41–42. |
| Billing 48 | **Accrual at official delivery.** Each batch accrues its full one-off share and its year-1 Care in the month of its official delivery, whatever was billed earlier as advance. |
| Billing 49 | **Advance.** Usually 50%, or 100%, of the contract's **one-off total plus year-1 Care**. It is invoiced when the contract is signed, due in 10 days, and **accrued only at official delivery**. The advance invoice is created outside this system. The signing date comes from CRM: the salesperson must enter it to mark the deal Won. Billing records the advance (percentage, amount, signing date) so that it can be offset. |
| Billing 50 | **Proportional offset by default.** Each batch is billed at (100% − advance %) of its value (one-off share plus year-1 Care). The billing team can **override the offset for a batch**. The system shows the advance still to be offset, the offsets always add up to the advance, and the last batch takes any rounding difference. |
| Billing 51 | **Full advance.** With a 100% advance, each batch is billed 0 but still accrues its value at official delivery. |

### Round J — D-ID (Digital ID / Security) (26 September 2026)

| Ref | Decision |
|---|---|
| Billing 52 | **Revenue type and joining rule are separate.** Every recurring line has a **revenue type** for reporting (Care/Maintenance, SaaS or SLA) and a **joining rule** for billing:<br>(A) **after year 1**: Qmatic Care, Billing 21–23;<br>(B) **units from the delivery month**: SLA, Billing 34–36;<br>(C) **aligned to the anniversary**: SaaS, Billing 41–42;<br>(D) **prepaid term, renewal by tender**: Billing 57–58.<br>The three settings (Billing 24) apply to rules A–C. A new rule can be added without changing the others. |
| Billing 53 | **One recurring contract per product line.** Each keeps its own anniversary. A customer with both a Mobile Token subscription and Ezio has two contracts. |
| Billing 54 | **Per-user SaaS.** The amount can be users × price per user per year, or a fixed annual amount. Users added mid-year are charged for the months left to the anniversary, including the delivery month, like a later project (Billing 42). From the next anniversary they are part of the annual total. Nothing is charged per transaction. |
| Billing 55 | **Mobile Token (NGT's own).** The **subscription** is SaaS with a fixed amount (not per user). **CAPEX + maintenance**: the CAPEX is a one-off, billed and accrued at official delivery; the maintenance is reported as Maintenance but uses joining rule C. For both, accrual and billing are each monthly or annual. The first project buys a full year from its official delivery and is billed by its billing pattern; with annual billing, that year goes on the CAPEX invoice. Later projects are aligned to the anniversary. |
| Billing 56 | **Vendor devices without maintenance** (USB PKI tokens, OTP tokens without a server subscription) are one-off only. |
| Billing 57 | **HSM maintenance is a prepaid term.** An HSM is sold with one or more years of maintenance. The CAPEX and all included maintenance years are billed and accrued together at official delivery; there is no recurring billing schedule. The system records the annual maintenance value, the years included and the **coverage end**. Each purchase keeps its own calendar, independent of the customer's other purchases. |
| Billing 58 | **Renewal by tender.** HSMs are sold mainly to public institutions, where each renewal is a separate tender, so a renewal is a **new sale**, not a Billing renewal.<br>• From the coverage end, **expected renewal revenue** equal to the original one-year maintenance value, per year, appears in forecasting and budgeting.<br>• **6 months before** the coverage end, the account owner and the direction manager are alerted, and a CRM opportunity ("Renewal tender") is **created automatically**. Its 12-month Maintenance amount equals the original one-year value.<br>• When the tender is won, it is billed as a new sale with its own prepaid term. |
| Billing 59 | **Advance configurable per contract, 0–100%** (revises Billing 49). Commercial customers are typically 50% or 100%; public institutions are usually 0%. At 0%, each batch is billed in full at its official delivery. This applies to every direction. |

### Round K — prototype gap review (27 September 2026)

| Ref | Decision |
|---|---|
| Billing 60 | **Handover document.** When entering the official delivery date, the accountant can attach the Revenue Service handover document to the batch as evidence. The document is optional; the date stays mandatory. The prototype's invoice upload, which reads an already-issued invoice to record what was delivered, is not adopted: here the order runs official delivery → billed item → handover → invoice outside the system. |
| Billing 61 | **Contract record.** Each recurring contract also records its contract number, term start and end, the customer's notice period (default 3 months) and the resulting **cancel-by date**, plus its documents. The cancel-by date shows on the contract and in Renewals, highlighted from 45 days before. For CEM Care, the acceptance window (Billing 27) still governs renewal; the cancel-by date is the customer's contractual deadline. *Adopted from the prototype's contract repository.* |
| Billing 62 | **System-prepared emails.** The billing-change email to accountants and the annual-quote cover email use the approval-gated outbox (Solution Architecture, Arch 19). The system prepares the email; a recipient or designated approver (Billing 65) reviews and edits it, opens it in their own mail app, sends it, and marks it sent or discards it. Preparation and the final step are audited. The system never sends email. *Adopted from the prototype.* |

### Round L — open questions answered (28 September 2026)

| Ref | Decision |
|---|---|
| Billing 63 | **SLA and SaaS renewal deadline.** For an SLA or SaaS contract without auto-renew (Billing 38, 44), the customer's acceptance is due by the contract's **cancel-by date** (term end minus the notice period, Billing 61). The billing team is reminded **60 and 30 days before** the cancel-by date. An auto-renewing contract needs no acceptance. |
| Billing 64 | **Escalation.** A billed item that is due and not handed over stays in the Billing / Accountant brief. After **5 working days** (configurable) it also appears in the **Executives'** brief until it is Done. |
| Billing 65 | **Outbox approvers.** An Admin names the designated approvers for each type of prepared email in Settings, for example the head accountant for billing changes and the direction manager for annual-quote emails. The email's recipients can always approve it. Changes to the approver lists are audited. |
| Billing 66 | **Accounting system.** NGT's accounting system is **1C**. Whether 1C can export invoice and payment status is being checked. Until then, Billing records no paid status (Billing 17), and nothing links to 1C. |

## 2. Purpose and boundaries

The module answers: what charge is expected, for which customer and scope, in which currency, when it is billed, how it accrues, what prerequisite remains, and whether it has been handed over for invoicing.

It does not generate invoices or credit notes, record payment, synchronize with accounting, collect money or reconcile payments. Done is a handover status. The accrual schedule is information for accountants, who book accruals in the accounting system.

Reporting rates never change contractual amounts. Sales value, billed amounts and paid amounts are never added together. **Renewals never create a CRM opportunity, a Won sale or a project.**

## 3. Ownership and workspaces

At launch the **Billing / Accountant** role covers both the central billing team and accountants.
- It manages schedules and enters official delivery dates.
- It confirms recalculations and marks items Done.
- It creates adjustments, records renewal acceptance and sends annual quotes.

Billing administrators maintain templates and presets. PMs confirm operational completion and send batches to the accountant.

| Workspace | Purpose |
|---|---|
| Billing calendar | Billed items by period, customer, direction, type and currency. Care contracts also show an accrual row. |
| Awaiting official delivery | Delivery batches sent by PMs. The accountant enters the official delivery date (Revenue Service sign-off) and sees each batch's allocation and advance offset. The handover document can be attached (Billing 60). |
| Handover queue | Items ready for handover or overdue, grouped by invoice, with blockers |
| Renewals | Care renewal acceptance (the four-month rule), annual quotes due, SaaS/SLA reminders, and contracts' cancel-by dates (Billing 61) |
| Billing changes | Differences over the next three months |
| Agreements and Care contracts | Terms, settings, sales, contract years, schedules, overrides and history |
| Change previews | Before/after previews awaiting confirmation |
| Adjustments | Corrections linked to Done items |
| Outbox | Prepared emails awaiting review, sending and marking (Billing 62) |
| Templates and presets | Template versions and Care presets, with preview cases (administrators) |

## 4. Records

| Record | Content |
|---|---|
| Billing agreement | Customer, commercial source, direction, covered scope, terms |
| **Care contract (CEM)** | Customer, direction, currency, preset, accrual pattern, billing pattern, anniversary month, auto-renew clause flag, contract number, term, notice period, cancel-by date (Billing 61) |
| **Care sale** | Source opportunity and recurring line, annual Care value, official delivery date, year-1 coverage (delivery month + 11) |
| **Contract year** | Period, annual Care total and its calculation, renewal acceptance (state, who, when, evidence), annual quote (prepared, sent, by whom), decision if no acceptance |
| Charge plan | Revenue type, template or preset, inputs, currency, term, linked scope and source line |
| Schedule item | Period, billing date, amount, currency, status, template version or override; **billed item** |
| **Accrual item** | Care contract, period, accrued amount; read-only information |
| **Invoice group** | Items handed over together as one invoice, such as a project one-off plus year-1 Care |
| **Supplementary Care charge** | Care contract, contract year, the late sale, months added, amount |
| **SLA contract** | Customer, direction, currency, settings (Billing 32), auto-renew flag, Billing 61 fields |
| **SLA line** | Unit type (branch, user, custom module), unit price, current units |
| **SLA change** | Source project (with or without sale value), units added or removed, official delivery date, start month (delivery month or next, with reason), free months |
| **SaaS contract** | Customer, direction, currency, settings, anniversary (first project's delivery month), auto-renew flag, Billing 61 fields |
| **SaaS project line** | Source project, annual value, official delivery date, aligned first-purchase period and amount |
| **Delivery batch** | Project, name, planned month, one-off share (optionally by HW / SW / PS), Care value, SLA units per line, SaaS annual value, free months, official delivery date and handover document, advance offset (proportional or overridden, with reason) |
| **Advance** | Contract, percentage (0–100%), base (one-off total plus year-1 Care), amount, signing date (from CRM), offset so far, remaining |
| **Recurring line** | Revenue type (Care/Maintenance, SaaS, SLA), joining rule (A–D), product line, amount basis (fixed annual amount, or units × unit price) |
| **Prepaid maintenance** (D-ID) | Purchase, annual maintenance value, years included, coverage end, expected renewal value (= annual value), alert date, linked renewal-tender opportunity |
| Override, handover record, adjustment, reminder, recalculation proposal, Upsell lead link | As in v3 |

## 5. Recurring engine and templates

**Presets for CEM / Qmatic**, all on the same three settings (Billing 32):

| Preset | Accrual | Billing | Anniversary | How a project enters | Renewal |
|---|---|---|---|---|---|
| Care · Type 1 Standard | Monthly | Monthly or annual | Configurable; default first delivery | Full year billed and accrued at official delivery, on the project invoice; joins after its first year | Acceptance always |
| Care · Type 2 Small | Annual | Annual | Configurable; default first delivery | As Type 1 | Acceptance always |
| SLA · Standard | Monthly | Monthly | Its own | Units added from the official delivery month (or the next, case by case), after any free months | Acceptance unless auto-renew |
| SaaS · Standard | Monthly | Annual | First project's delivery month | First project: a full year. Later projects: aligned to the anniversary | Acceptance unless auto-renew |

**Presets for D-ID** (joining rules per Billing 52):

| Product | Revenue type | Joining rule | Accrual / billing | Notes |
|---|---|---|---|---|
| Mobile Token subscription (own) | SaaS | C · aligned | Monthly or annual, each | Fixed amount |
| Mobile Token maintenance (own, with CAPEX) | Care/Maintenance | C · aligned | Monthly or annual, each | CAPEX is a one-off at official delivery |
| Vendor SaaS (e.g. Ezio) | SaaS | C · aligned | Monthly or annual, each | Users × price; added users aligned |
| HSM maintenance (vendor) | Care/Maintenance | D · prepaid term | Billed and accrued with the CAPEX | Forecast, alert and renewal tender |
| USB PKI / OTP tokens (vendor) | — | — | One-off | No maintenance |

### 5.1 CEM / Qmatic Care (Billing 20–31)

**Worked example.** Two sales, USD, Type 1 preset, February anniversary:
- Sale 1: annual Care value 12,000. Official delivery February 2025, so year 1 runs Feb 2025 – Jan 2026.
- Sale 2: annual Care value 6,000. Official delivery March 2025, so year 1 runs Mar 2025 – Feb 2026.

| Period | Accrued (Type 1) | Billed (Type 1, monthly) | Billed (Type 1, annual) | Accrued and billed (Type 2) |
|---|---|---|---|---|
| Feb 2025 | 12,000 | 12,000 with the project invoice | 12,000 with the project invoice | 12,000 |
| Mar 2025 | 6,000 | 6,000 with the project invoice | 6,000 with the project invoice | 6,000 |
| Apr 2025 – Jan 2026 | — | — | — | — |
| **Contract year Feb 2026 – Jan 2027**: annual Care total 12 × 1,000 + 11 × 500 = **17,500** | | | | |
| Feb – Dec 2026 | 1,458.33 each | 1,458.33 each | 17,500 in Feb 2026 | 17,500 in Feb 2026 |
| Jan 2027 | 1,458.37 (takes the rounding) | 1,458.37 | — | — |
| **Contract year Feb 2027 – Jan 2028**: 12,000 + 6,000 = **18,000** | | | | |
| Each month | 1,500 | 1,500 | 18,000 in Feb 2027 | 18,000 in Feb 2027 |

**Same sales, January anniversary.** The 2026 contract year counts sale 1 from February to December and sale 2 from March to December: 11,000 + 5,000 = **16,000**. Monthly, that is 1,333.33, with December at 1,333.37.

**Late delivery (Billing 30).** Sale 3 has an annual Care value of 2,400. Its official delivery is on 20 January 2026, after the annual quote for Feb 2026 – Jan 2027 was sent. Year 1 runs Jan – Dec 2026 and is billed and accrued in January 2026 (2,400). It adds January 2027 to the quoted year, so a **supplementary Care charge of 200** is created. The next contract year's total is 12,000 + 6,000 + 2,400 = **20,400**.

**Renewal timeline** for a February anniversary:

| When | Step |
|---|---|
| Up to September | On track |
| October – November (4–3 months before) | **Acceptance due**: the customer must confirm explicitly |
| From December (2 months before), no acceptance | **Overdue**: case-by-case decision (Billing 28) |
| January (1 month before) | **Annual quote** sent with the annual Care total |
| February | Contract year starts; accrual and billing follow the contract's settings |

**Calculation rules:**
- Whole months are used throughout.
- Decimal-safe arithmetic; 2 decimals per item; the last month takes the rounding difference.
- Every billed item and accrual item stores the calculation behind it.
- An override is possible with a reason (Billing 11), and a recalculation shows it in the preview.
- A change to settings or the anniversary applies from the next contract year and goes through a preview.

### 5.2 CEM / Qmatic SLA (Billing 33–39)

**Worked example.** One SLA line at 150 GEL per branch; monthly accrual and billing.
- **Project 1:** 40 branches, official delivery 12 Feb 2025, 2 free months.
- **Launch without a sale:** 1 more branch, official delivery 20 Jun 2026, 1 free month.

| Period | Billed and accrued | Why |
|---|---|---|
| Feb – Mar 2025 | 0 | Project 1's free months |
| Apr 2025 – Jun 2026 | 6,000 a month | 40 × 150. The new branch's free month is June 2026. |
| From Jul 2026 | 6,150 a month | 41 × 150 |

If the accountant had set the launch to start the following month, its free month would be July and 6,150 would start in August.

**Rules:**
- Whole months throughout.
- A quantity change is always tied to an official delivery (Billing 35).
- Price changes, including negotiated indexation, go through a preview and apply from a stated month.
- Done items are corrected only by adjustments.

### 5.3 CEM / Qmatic SaaS, resold (Billing 40–44)

**Worked example.** Standard preset (annual billing, monthly accrual), USD.
- **Project 1:** annual value 12,000, official delivery February 2025. This sets a February anniversary.
- **Project 2:** annual value 6,000, official delivery June 2025. It is aligned to February: June 2025 to January 2026 is 8 months.

| Period | Billed | Accrued |
|---|---|---|
| Feb 2025 | 12,000 (project 1, full year) | 1,000 a month, Feb 2025 – Jan 2026 |
| Jun 2025 | 4,000 (project 2: 6,000 × 8/12) | +500 a month, Jun 2025 – Jan 2026 |
| Feb 2026 | 18,000 (annual total) | 1,500 a month, Feb 2026 – Jan 2027 |

With monthly billing, the same amounts would be billed month by month as they accrue.

### 5.4 CEM / Qmatic project charges: batches and advance (Billing 45–51)

**Worked example.** A 100-branch agreement, USD, signed March 2026, with a 50% advance.
- One-off 500,000: hardware (HW) 200,000, licences (SW) 150,000, installation and configuration (PS) 150,000 (1,500 per branch).
- Annual Care 30,000.
- SLA 100 per branch per month.

The advance is 50% × (500,000 + 30,000) = **265,000**, invoiced outside the system at signing and due in 10 days.

| When | Batch | Accrued | Billed (proportional offset) | Recurring effect |
|---|---|---|---|---|
| Mar 2026 | Signing | 0 | Advance 265,000 (outside the system) | — |
| Mar 2026 | 1 · all hardware | 200,000 | 100,000 | — |
| Jun 2026 | 2 · all licences and Care | 150,000 + year-1 Care 30,000 | 90,000 | Joins the Care contract from Jun 2027 |
| Jul 2026 – Apr 2027 | 3–12 · installation, 10 branches each | 15,000 each | 7,500 each | SLA +10 branches from each batch's delivery month |
| **Total** | | **530,000** | **265,000 + 265,000 = 530,000** | |

With an override, the billing team might bill batch 1 in full and take more of the advance off later batches. The remaining advance to offset is always shown, and the total still reaches 530,000. With a 100% advance, every batch is billed 0 and still accrues as above.

### 5.5 D-ID (Billing 52–59)

**HSM, public institution, 0% advance.** Official delivery April 2026: CAPEX 80,000 USD plus 3 years of maintenance at 12,000 a year.

| When | What happens |
|---|---|
| Apr 2026 | One invoice: 80,000 + 36,000 = **116,000**, billed and accrued. Coverage runs to the end of March 2029. |
| 1 Oct 2028 | Alert to the account owner and direction manager; CRM opportunity "Renewal tender" created with Maintenance of 12,000 a year |
| From Apr 2029 | Expected renewal revenue of 12,000 a year in forecasting and budgeting until the tender is won or lost |

**Ezio, per user, annual billing, monthly accrual.** 20,000 users × 2 USD a year, official delivery January 2026, so the anniversary is January.

| When | Billed | Accrued |
|---|---|---|
| Jan 2026 | 40,000 | 3,333.33 a month (December 3,333.37) |
| Sep 2026: +5,000 users | 5,000 × 2 × 4/12 = **3,333.33** (Sep – Dec) | +833.33 a month (December 833.34) |
| Jan 2027 | 25,000 × 2 = 50,000 | 4,166.67 a month (rounding in December) |

**Mobile Token CAPEX + maintenance, annual billing, monthly accrual.** Official delivery May 2026: CAPEX 30,000 GEL and maintenance of 6,000 a year. The CAPEX invoice carries both, **36,000**. The CAPEX accrues 30,000 in May; the maintenance accrues 500 a month from May 2026 to April 2027. The anniversary is May.

### 5.6 Other directions and types (provisional)

| Type | Template (as in v3) | Status |
|---|---|---|
| Care, other directions (e.g. vendor hardware maintenance) | Annual amount (fixed or % of a base), anniversary, batches | Provisional; to be defined direction by direction |
| SLA and SaaS, other directions | v3 templates | Provisional; CEM/Qmatic rules are the likely starting point |
| One-off / deposit / milestone (directions without batch rules yet) | Amount or % and basis, due date or triggering event; items sum to the agreed amount | Kept for those directions; CEM and D-ID use batches and advances (Billing 45–51, 59) |

## 6. Triggers

| Charge | Trigger |
|---|---|
| Project one-off plus **year-1 Care** (CEM) | Official delivery date entered by the accountant (Billing 20–21); one invoice |
| **Care, year 2 onwards** (CEM) | Contract year start, after renewal acceptance or a recorded decision to continue (Billing 27–28) |
| **Supplementary Care charge** | Official delivery that adds months to an already-quoted contract year (Billing 30) |
| **Batch invoice** (CEM) | Official delivery of the batch: one-off share plus year-1 Care, minus its advance offset (Billing 45–50) |
| **Advance** (all directions) | Signing date entered in CRM to mark Won; 0–100% per contract; invoiced outside the system; recorded for offsetting (Billing 49, 59) |
| **SaaS users added** (D-ID) | Official delivery of the added users; aligned to the anniversary (Billing 54) |
| **HSM with prepaid maintenance** (D-ID) | Official delivery: CAPEX plus all included maintenance years on one invoice (Billing 57) |
| **Renewal tender alert and opportunity** (D-ID) | 6 months before the coverage end (Billing 58) |
| **SLA start or quantity change** (CEM) | Official delivery of the project, including a project with no sale value (Billing 34–35); after its free months (Billing 36) |
| **SaaS first project** (CEM) | Official delivery; a full year; sets the anniversary (Billing 41) |
| **SaaS later project** (CEM) | Official delivery; aligned to the anniversary (Billing 42) |
| **SLA / SaaS renewal** (CEM) | Contract year start; acceptance first unless auto-renewing (Billing 38, 44) |
| Deposit (directions without batch rules yet) | Agreed date or confirmed contractual event |
| Milestone (directions without batch rules yet) | The identified milestone and its confirmations, or an agreed fixed date |
| Recurring types in other directions | As in v3, under review |

A date arriving never overrides an outstanding confirmation. Partial delivery affects only its batch.

## 7. Dates to keep distinct

- PM delivered date.
- Sent to accountant.
- **Official delivery date** (Revenue Service sign-off, entered by the accountant) and the time it was entered.
- Year-1 coverage.
- Contract year and anniversary.
- Acceptance due window and acceptance date.
- Quote sent date.
- Cancel-by date (Billing 61).
- Billing date and accrual period of each item.
- Done time.

A backdated official delivery produces a visible catch-up preview and, where Billing 30 applies, a supplementary charge.

## 8. Changes and recalculation

Unchanged from v3:
1. Identify affected items that are not yet Done.
2. Preview them, including overrides.
3. Confirm.
4. Keep the prior calculation.
5. Notify.

Done items are corrected only by adjustments. For CEM Care, a change to the settings or anniversary takes effect from the next contract year.

## 9. Handover, Done and corrections

Flow: **Planned → Awaiting prerequisite / Ready for handover → Done**. Items that go on one invoice, such as a project one-off and year-1 Care, are handed over together as an invoice group. A Done item is never overwritten; corrections are linked adjustments.

## 10. Renewals, upsells and reminders

- **CEM Care:** acceptance always required (Billing 27), case-by-case decision when missing (Billing 28), annual quote 1 month ahead (Billing 29).
- **CEM SLA and SaaS:** an auto-renewing contract continues; otherwise acceptance is required before the next contract year (Billing 38, 44). Acceptance is due by the contract's cancel-by date, with reminders 60 and 30 days before it (Billing 63).
- **Upsells:** unchanged; a new recurring type or new one-off scope becomes a CRM Upsell lead.
- **Reminders:** due items not handed over remind the billing team, then escalate to the Executives after 5 working days (configurable; Billing 64).

## 11. Won reversal

Unchanged: not-yet-Done items move to Awaiting review; Done items are untouched.

## 12. Functional review scenarios

1. Official delivery entered as 12 Feb 2025 creates one invoice group: the project one-off plus year-1 Care of 12,000. Both are billed and accrued in February 2025.
2. A second sale delivered in March 2025 joins the same Care contract, whose anniversary stays February.
3. The 2026 contract year totals 17,500: 11 months × 1,458.33 plus 1,458.37 in January 2027.
4. With annual billing on the same Type 1 contract, one billed item of 17,500 appears in February 2026, while accruals stay monthly.
5. A Type 2 contract shows both billed and accrued as 17,500 in February 2026.
6. Changing the anniversary to January gives 16,000 for 2026, previewed first and applied from the next contract year.
7. With no acceptance by December for a February anniversary, the contract shows Overdue and asks for a recorded decision.
8. The annual quote is prepared in January; a person sends it and marks it sent.
9. A delivery entered on 20 January 2026 creates a supplementary charge of 200 without changing the quoted 17,500.
10. The PM marking Delivered creates no Care charge; only the official delivery date does.
11. No billing screen shows supplier costs, margins or payments.
12. An SLA starts in the month of official delivery; after 2 free months, 40 × 150 = 6,000 is billed and accrued from April 2025.
13. A branch launched without a sale, through a project with no sale value, adds 150 a month after its free month.
14. The accountant sets a launch to start the following month; the reason is recorded and the free month moves with it.
15. A second SaaS project delivered in June is billed 4,000 for June–January, then joins the 18,000 annual total in February.
16. A non-auto-renewing SLA without acceptance does not continue into the next contract year; an auto-renewing one does.
17. A deal cannot be marked Won in CRM without a signing date; the signing date sets up the advance record.
18. With a 50% advance on 530,000, hardware delivered first (200,000) is billed 100,000 and accrues 200,000.
19. Batch 2 (licences 150,000 plus Care 30,000) is billed 90,000; its Care joins the Care contract after its own first year.
20. Overriding one batch's offset changes the remaining advance shown; the offsets still add up to 265,000.
21. With a 100% advance, every batch is billed 0 and accrues its full value at official delivery.
22. The project cannot be officially delivered without a warning while part of the contract totals is unallocated to batches.
23. An HSM sale with 3 years of maintenance and 0% advance is billed and accrued as 116,000 at official delivery; no recurring items are created.
24. Six months before the HSM coverage ends, the alert fires and a "Renewal tender" opportunity appears in CRM with 12,000 Maintenance.
25. From the coverage end, 12,000 a year of expected renewal revenue appears in forecasts until the tender is decided.
26. Adding 5,000 Ezio users in September bills 3,333.33 for September to December; the next annual total is 50,000.
27. A customer with Mobile Token and Ezio has two recurring contracts with different anniversaries.
28. A public-institution contract with 0% advance bills each batch in full at official delivery.
29. The accountant enters an official delivery date and attaches the handover document; the batch shows both. Entering the date without a document is also accepted.
30. A contract whose term ends on 31 March 2027, with a 3-month notice period, shows a cancel-by date of 31 December 2026, highlighted from 16 November 2026.
31. The billing-change email is prepared in the outbox, edited by an accountant, sent from their own mail app and marked sent; the audit shows the preparation and the sending.
32. An SLA contract without auto-renew, ending 31 March 2027 with 3 months' notice, has acceptance due 31 December 2026, with reminders on 1 November and 1 December 2026.
33. An item due on Thursday 1 October and not handed over appears in the Executives' brief from Thursday 8 October, 5 working days later.
34. A billing-change email can be sent only by one of its recipients or an approver named for billing-change emails; an Admin who is neither cannot send it.

## 13. Open items

- **Auto-renew flag for CEM Care:** acceptance is always required, so what does the contract's auto-renew clause change, if anything?
- Who decides when acceptance is missing (proposed: the direction manager)?
- The billing and accrual month of a supplementary charge (proposed: the first month it covers).
- Sales in different currencies within one customer's Care contract.
- **Type 3 · Large public organisation:** its own flow, to be defined.
- **SLA:** when a reduction (a branch closing) takes effect; how mid-year changes are billed on an SLA billed annually (exceptions to define later).
- **SLA and SaaS renewal:** whether an annual quote is sent as for Care (the deadline is decided, Billing 63).
- **1C:** whether it can export invoice and payment status (Billing 66).
- **Indexation process** for SLA, and how vendor price changes on resold SaaS are handled at renewal.
- The other directions: Care, SLA and SaaS rules.
- **Cross-module (PM):** a project with no sale value (Billing 35) needs a way to be created without a Won opportunity, linked to the customer's SLA contract.
- **Cross-module (PM):** delivery batches replace the v3 "delivery scopes". Each batch also carries recurring allocations (Care value, SLA units, SaaS value, free months). The batch-splitting screen needs design work to be easy to use.
- **Cross-module (CRM):** Won requires a **signing date** (Billing 49). This changes CRM v3 §6.
- **Cross-module (CRM):** the automatic **"Renewal tender" opportunity** (Billing 58) is an exception to CRM 19/48, which say renewals are never CRM opportunities. CRM needs this opportunity type, and forecasting needs the expected renewal revenue.
- **Type 3 (large public) Care** may follow the same tender pattern; to be checked when it is defined. Salespeople can already open a Renewal tender manually for such renewals (CRM 83); how Billing treats the Care contract then is to be defined with Type 3.
- Accounting treatment of multi-year prepaid maintenance accrued in full at delivery (like year-1 Care): to be confirmed with the accountant.
- **Cross-module (Commercial):** the advance percentage belongs in the accepted terms.
- **Advance item:** should accountants still see an "advance to invoice" item after Won, as a reminder with a trace, even though the invoice itself is created outside? *Proposed: yes, as an information item that needs no handover.*
- Does the advance base include a resold SaaS first purchase billed at delivery, as it includes year-1 Care?
- Accounting treatment of year-1 Care accrued at delivery rather than across the months it covers: to be confirmed with the accountant.
- The handover format; cancellations and pauses; reversing an official delivery.

**Sources:** Billing_Module_v3.md to v3.3; CEO decisions of 26 September 2026 on CEM/Qmatic (Care, SLA, SaaS, delivery batches, advances) and D-ID, with the worked examples in "Billing Scenarios – 3 Types of Care"; CRM, PM and Access v3; the prototype gap review (NGT_CRM_Gap_Register, 27 September 2026) and CEO confirmation of the adopted rules; the CEO's answers to the open questions of change request CR-2026-09 rev. 4 (28 September 2026).
