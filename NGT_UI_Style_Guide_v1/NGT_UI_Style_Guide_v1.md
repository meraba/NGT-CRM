# NGT UI Style Guide — v1

**28 September 2026 · for any new NGT prototype or design page**
**Source:** Luka Geldiashvili's NGT CRM prototype (`src/styles.css` and screens, commit 89d1d2a), reviewed against the v3.3 design documents. This guide replaces *UI_Reference_Luka_Prototype.md*, which had no stylesheet or screenshots to work from.

**Files that come with this guide:**
- `ngt-ui-tokens.css`: the design tokens and core components, taken from the prototype, plus a proposed dark theme and a Kiosks tag.
- `ngt-starter.html`: a one-page starter (shell, Morning Brief, table, board) built only from those tokens, with fictional data. Open it next to `ngt-ui-tokens.css`.
- `screenshots/`: ten reference screens of the prototype (list in §11).

---

## 1. How to use this guide

1. **Keep the look.** New prototypes use these tokens, type sizes and components, so everything feels like one NGT system. Copy `ngt-ui-tokens.css` (or paste it into a `<style>` block when a single-file page is needed).
2. **Keep the business rules current.** The prototype's screens show some rules that have since changed. Build from the v3.3 documents, apply §9, and don't copy anything in §10.
3. **Use fictional data.** The screenshots show the prototype's seed, which uses real customer names. New prototypes use fictional customers, people and ID numbers (Solution Architecture, Arch 13).
4. **Build light prototypes, one area at a time.** Plain HTML, CSS and JavaScript with no build step, as the prototype does. A focused prototype of one screen or workflow is better than another full app.
5. **Anything not given here, keep in character:** plain, dense, calm and accessible (§2). Mark new tokens or components as *proposed*.

## 2. Character

- **An operational tool.** Dense, practical screens for about ten staff who use it all day. It is not a marketing site: no hero sections, gradients or decoration.
- **Calm neutrals, one accent.** Blue-grey neutrals, a deep green accent (`#0C5C48`) and a dark navy sidebar. Colour is used mainly for state.
- **Numbers are first-class.** Amounts use a monospaced face with tabular figures, and always carry their currency (₾ for GEL).
- **Plain web technology.** A single page, system fonts, inline SVG icons, and no framework or external libraries.
- **Accessible.** Visible keyboard focus, and colour is always paired with text or shape. Toasts are announced to screen readers, and every chart has a table twin.
- **Bilingual:** English, with Georgian for menus, titles and main buttons (a language switch).
- **Responsive:** below 900 px the sidebar becomes a slide-in menu and grids stack.

## 3. Colour tokens

Defined on `:root` in `ngt-ui-tokens.css`. The prototype is light-only; the dark values in the file are **proposed**.

| Token | Light | Role |
|---|---|---|
| `--ground` | `#F7F9FB` | Page background |
| `--surface` | `#FFFFFF` | Cards, tables, top bar, modals |
| `--border` | `#DFE5ED` | All borders, 0.5 px hairlines |
| `--ink` | `#0F1C2E` | Primary text |
| `--ink-2` | `#5A6A7A` | Secondary text, labels |
| `--ink-3` | `#98A6B5` | Muted text, uppercase labels, placeholders |
| `--accent` / `--accent-hover` / `--accent-tint` | `#0C5C48` / `#0A4F3E` / `#E5F2EE` | Primary buttons, active tab, links, "done" state, key values |
| `--sidebar` / `--sidebar-hover` / `--sidebar-text` | `#141F2E` / `#1B2F42` / `#8FA4B8` | Dark navigation column |
| `--blue` / `--blue-tint` | `#2563A8` / `#EBF2FC` | In progress, informational, status changes |
| `--amber` / `--amber-tint` | `#C97B22` / `#FDF3E3` | Due soon, pending, awaiting, billing |
| `--orange` / `--orange-tint` | `#B85C1A` / `#FBF0E8` | Waiting on someone, negotiation |
| `--red` / `--red-tint` | `#C23B3B` / `#FCEAEA` | Overdue, lost, errors, flags |
| `--green` / `--green-tint` | `#1A7A53` / `#E6F4EE` | Won, delivered, positive change |

**State colours** (chips carry a dot and a text label; colour is never the only signal):

| Meaning | Chip class | Colour |
|---|---|---|
| Not started, neutral, Lead | `ch-todo`, `ch-lead` | Grey on `#EAEEF2` |
| In progress, Qualified, informational | `ch-wip`, `ch-qual` | Blue |
| Due soon, pending, proposal out | `ch-soon`, `ch-pend`, `ch-prop` | Amber |
| Waiting on others, negotiation | `ch-wait`, `ch-neg` | Orange |
| Overdue, lost | `ch-ovr`, `ch-lost` | Red |
| Done, handed over | `ch-done` | Accent green |
| Won, delivered | `ch-won`, `ch-del` | Green |

**Direction tags** (small uppercase tags next to account and deal names):

| Direction (v3 label) | Class | Colours |
|---|---|---|
| CX / Queue management (Qmatic) | `dq` | `#1E5B96` on `#E5EFF9` |
| Digital ID / Security | `dd` | `#6B3EAB` on `#EEE5F9` |
| Cash handling | `dk` | `#5A5230` on `#F0EEE5` |
| Digital Signage (was CMS) | `dc` | `#2A7A3D` on `#E5F3E7` |
| VOIX + CF (was Voix/CF) | `dv` | `#9A5A10` on `#FBF0E0` |
| Kiosks (*proposed*, not in the prototype) | `dki` | `#1D6570` on `#E3F2F4` |
| General / account-wide | `dg` | `#5A6A7A` on `#EEF1F5` |

**Charts:** a single hue, `#2a78d6`, for one measure; `#1a9a6c` for "new" against `#2a78d6` for "delivered" in two-series charts. The palette was checked for colour-blind safety.

## 4. Typography

| Use | Font | Size / weight |
|---|---|---|
| Everything | `--font`: 'Segoe UI', system-ui, -apple-system, sans-serif | Body 13 px / 400, line height 1.5 |
| Numbers, amounts, counts, IDs | `--mono`: 'Cascadia Code', Consolas, 'Courier New', monospace | Tabular figures |
| Page title | Sans | 20 px / 600, letter-spacing −0.01em |
| Page subtitle | Sans | 13 px, `--ink-2` |
| Card and section title | Sans | 13 px / 600 |
| Uppercase labels (table headers, card labels, brief sections, sidebar groups) | Sans | 10 px / 600, uppercase, letter-spacing 0.06–0.08em, `--ink-3` |
| Stat value | Mono | 26 px / 700 |
| Board card value | Mono | 14 px / 700, accent |
| Chips | Sans | 11 px / 600 |
| Buttons | Sans | 12 px / 600 |
| Modal title | Sans | 15 px / 700 |

The screenshots were rendered where Segoe UI isn't installed, so they show a fallback face. On Windows the prototype renders in Segoe UI.

## 5. Shape, spacing and depth

- **Radii:** 12 px on cards (`--radius`); 14 px on modals; 8 px on buttons, inputs and board cards; 7 px on icon buttons and tabs; 20 px on chips; 4 px on direction tags.
- **Borders:** 0.5 px hairlines in `--border`. There are no heavy borders.
- **Depth:** flat. Shadows only on a hovered board card, toasts and the mobile slide-in menu.
- **Spacing:**
  - Content padding 26 px × 28 px.
  - Card header 14 px × 20 px.
  - Table cells 10 px × 16 px.
  - Gaps between cards 14–18 px.
- **Accent stripes carry meaning, not decoration.** A 3 px left stripe marks a stat card's kind, a brief item's section and a flagged board card (red inset for "needs attention").

## 6. App shell and navigation

| Element | Decision |
|---|---|
| Sidebar | 220 px, dark navy. NGT logo mark on top. Grouped navigation with small uppercase group labels: *My day* (Morning Brief, Tasks), *Sales* (Pipeline / Leads, Companies), *Delivery* (Projects, Financials), *Revenue* (Recurring / Billing), *Insights* (Dashboard, Reports). Settings and the signed-in user sit at the bottom. The active item has a 2.5 px accent bar on the left. |
| Top bar | 54 px, white. Breadcrumbs on the left (current page in bold). Search with a Ctrl K hint, a notification bell with a red dot, and the avatar on the right. |
| Screens | One page, one active screen. Detail pages have breadcrumbs. |
| Tabs | Underlined tabs with count badges on detail pages (`ptab`). Tabs that don't fit move into a **More** menu. Segmented sub-tabs (`stab`) switch views inside a screen. |
| Feedback | Toasts bottom right confirm actions; there are no blocking pop-ups. |
| Narrow screens | Below 900 px, a slide-in sidebar, a sticky top bar and stacked grids. |

## 7. Components

All are in `ngt-ui-tokens.css` with the prototype's class names.

| Component | Classes | Notes |
|---|---|---|
| Page header | `ph`, `ph-title`, `ph-sub` | Title and subtitle on the left; primary action on the right |
| Buttons | `btn btn-primary`, `btn btn-outline`, icon button `ib` | One primary per area |
| Stat cards | `stats-row`, `stat-card c-accent / c-neutral / c-amber / c-red`, `stat-label`, `stat-val`, `stat-delta up / dn` | Four in a row; a coloured left stripe by kind |
| Section card | `sc`, `sc-head`, `sc-title`, `sc-action` | The main container: white, hairline border, header row |
| Table | `tw` (scroll wrapper), `table`, `th.r` / `td.r` for numbers, `td.dim`, `td.muted` | Uppercase 10 px headers; right-aligned mono numbers; row hover |
| Chips | `chip ch-*` with a `dot` | States from §3 |
| Direction tags | `dir dq / dd / dk / dc / dv / dki / dg` | Next to account or deal names |
| Owner | `ow`, `ow-av` | 17 px initials avatar plus name |
| Tabs | `ptabs`, `ptab` (+ count), `stabs`, `stab` | As §6 |
| Property rail | `co-prop-row`, `co-prop-label`, `co-prop-val` | Left rail on deal and company pages: uppercase label over value |
| Kanban board | `board-wrap`, `board-col`, `board-col-hd` (name, count, mono total), `board-cards`, `board-card` (company, title, mono value, footer with tag and date), `board-card.stale` | Columns 210 px; drag and drop between stages |
| Morning Brief list | `brief-sec` (uppercase section with count), `brief-item k-status / k-stale / k-billing / k-tasks`, `brief-title`, `brief-sub` | Chip and direction tag on the right; colour stripe by section |
| Modal | `modal-ov`, `modal-panel`, `modal-hd`, `modal-bd`, `modal-ft` | Footer on the ground colour; actions right-aligned |
| Form fields | `fg` (2-column grid), `ff`, `fl` (label), `fi` (input or select) | Accent focus ring |
| Toasts | `toasts`, `toast`, `toast-ic`, `toast.warn` | Dark toast, green or amber icon; respects reduced motion |

Components seen in the screenshots but not in the CSS file are timelines (activity feeds), 12-month grids (Recurring) and SVG charts. Rebuild them from the screenshots with the same tokens.

## 8. UI decisions to keep

1. **The Morning Brief is the home screen.** One list per person, capped at 10, status changes first, fair rotation, and every section shows its full count. "Mark as seen" clears status changes only.
2. **Pipeline board and list.** A kanban board per direction with drag and drop, plus a list view. Cards show company, title, value (one-off) and flags.
3. **Deal page:**
   - a header (company / deal title) and a stage stepper with a "Move stage" action;
   - a left property rail;
   - a generated one-line summary with its flags;
   - quick-log buttons (Note, Email, Call, Meeting, Task);
   - tabs with counts;
   - a stage log that can't be edited.
4. **Company page scoped by direction.** One selector (all directions or one) filters every tab; one row per direction with its status and renewal state; cross-sell hints.
5. **Tasks grouped by urgency** (Overdue / Today / Next 7 days / Later), with a calendar view.
6. **Projects board** by delivery stage, with *Send to accountant* and *Take back*. Official delivery is entered only on the finance side, never on the Projects board: sensitive actions live on one screen.
7. **Recurring grids:** month columns with subtotals, and changes highlighted (a red column header and cell, with an old → new tooltip) rather than every value.
8. **Prepared emails are never sent by the system:** *Review & send* → edit → *Open in mail app* → *I sent it* or *Discard*.
9. **Dashboards:** a few stat tiles and short ranked lists, not long tables.
10. **Charts:** SVG, one hue per measure, keyboard-reachable tooltips and a table twin.
11. **Hide, don't delete:** a switched-off feature disappears completely, with no dead links or empty menus.
12. **Wording:** short, plain labels; statuses written as states ("With accountant", "Ready to send"); every amount with its currency.

## 9. What the v3.3 rules change in the UI

| Area | Show this |
|---|---|
| Directions | Six, with the labels in §3; "Direction" replaces "Product" |
| Pipeline | Lead 5% → Qualified 10% → Solution/Demo 25% → (PoC/Pilot 35%) → Proposal sent 50% → (Tender/Procurement 60%) → Negotiation 75% → Contract signing 90% → Won / Lost; paused states Nurture, Postponed, Cold |
| Ownership | One **Owner** per deal; "Created by" kept as history. No "Contact Person". |
| Deal value | **One-off** and **12-month recurring** always shown separately; a labelled "First-year value" only on the deal page |
| Deal flags | Missing next action, Overdue next action, Expected close passed, Contact coverage (no contact, or one contact above 1,000,000 GEL of one-off or recurring) |
| Next action | A dated task on every open deal; it replaces the free-text "next step" and the 5/30-day stale rule |
| Won | The dialog asks for the **signing date** (required), the accepted proposal revision, the advance % and the delivery type; the reason is optional. The amounts are then locked. |
| Changes after Won | An **amendment** with an effective month (recorded by the Owner, the direction manager or the project's PM); the project shows sold / amended / allocated / delivered |
| Projects | **Delivery batches** with allocations and an "unallocated" indicator; each batch runs Working → Waiting → Delivered → Sent to accountant → Official delivery |
| Official delivery | The accountant **enters the official delivery date** (Revenue Service sign-off) and may attach the handover document |
| Billing grids | A **billed row and an accrued row**, contract years with navigation, settings per contract |
| Billing states | Planned → Awaiting prerequisite / Ready for handover → **Done** (handed over); corrections as linked adjustments. Never "sent / paid". |
| Renewals | Amber and red states measure the customer's **renewal acceptance**; the annual quote is a separate step; SLA and SaaS acceptance is due by the cancel-by date; **Renewal tender** deals |
| Morning Brief | Adds next actions, flags, Cold suggestions, returning Postponed and Nurture deals, batches awaiting official delivery, acceptances and quotes, renewal tenders, advances to invoice, escalations (Executives) and **Emails to approve** |
| Access | Screens, search, totals and exports show only what the user's role grants. Direction managers and Executives can open other people's briefs, read-only. |
| Customer status | Per direction, derived: Prospect / Active / Former, plus an overall status for display |

## 10. Don't copy from the prototype

These appear in the screenshots but contradict the v3.3 rules:
- A single deal **Value** that adds one-off and 12 × MRR. Use separate one-off and recurring values.
- The **Handshake** and **Frozen** stages, and fixed stage percentages that ignore an override.
- **Deal Owner + Contact Person**, and the "Probability of delivery this year" field.
- **"Stale"** badges from idle days; the "60+ days in stage" and "unpaid invoices" risks.
- The **invoice strip** (not sent → sent → paid), receivables ageing and "Payment overdue" items.
- The **health score**, product catalogue and quotes, forecast categories (Commit / Best case), the automation-rule editor, custom fields and the report builder.
- **"Mark sold"** and the PM's Delivered date used as the billing start.
- Admin seeing every value, every brief and every audit entry.

## 11. Reference screenshots

The prototype at 1440 × 900, seed data, signed in as the admin. They show the look, not the current rules (§10).

| File | Screen | Look for |
|---|---|---|
| `01_morning_brief.png` | Morning Brief | Person cards, section headers with counts, stripes, chips on the right |
| `02_leads_board.png` | Leads board | Column headers with counts and mono totals, cards, flags |
| `03_deal_page.png` | Deal page | Stage stepper, property rail, summary line, quick-log buttons, tabs with counts |
| `04_company_page.png` | Company page | Direction selector, per-direction rows, tabs |
| `05_dashboard.png` | Dashboard | Stat tiles, ranked lists, target meters |
| `06_projects.png` | Projects | Delivery-stage board, handover actions |
| `07_recurring_sla_grid.png` | Recurring, SLA | 12-month grid, subtotals, change highlighting |
| `08_tasks.png` | Tasks | Urgency groups, reminders, assignee |
| `09_reports_growth.png` | Reports | Recurring growth chart and table twin |
| `10_phone_brief.png` | Brief at 400 px | Narrow layout |

## 12. Suggested instruction for a prototype request

> Build this as a light, single-page HTML prototype in the NGT visual style: use the tokens and component classes in the attached `ngt-ui-tokens.css` (paste them into a `<style>` block if the page must be one file), follow the NGT UI Style Guide v1 (§6–§9), and don't copy anything in its §10. Use fictional customers and people. Follow the business rules in the attached v3.3 documents; where the prototype's screenshots and the documents differ, the documents win.
