# SafeBuild Cloud — Project Documentation

**Building Safety Platform** — a complete set of high-fidelity HTML prototypes for a UK building safety & compliance management SaaS, covering contractor management, risk management, building- and property-level compliance dashboards, and portfolio-wide compliance programmes.

> This document is the full project reference. For a quick start, see [README.md](README.md).

---

## 1. Project Overview

SafeBuild Cloud is designed for UK social housing providers and building owners who must comply with the Building Safety Act 2022, Fire Safety Regulations, Gas Safety (Installation and Use) Regulations, HHSRS, and related standards. The prototypes model three altitudes of the product:

1. **Portfolio level** — organisation-wide compliance programmes (e.g. a 10,000-property gas programme)
2. **Building level** — per-building compliance registers and safety cases (e.g. *Riverside House*)
3. **Property level** — per-dwelling safety dashboards (e.g. *Flat 12, Oak Court*) for gas, electrical, fire, alarms, damp & mould, HHSRS, and energy

A parallel **Contractor** module models the supply side: marketplace, onboarding, profiles, and job history.

### Tech approach

- Every screen is a **single self-contained `.html` file** — inline CSS, inline SVG, no build step, no framework
- Only external dependency: the **Inter** typeface from Google Fonts
- All charts (bar, line, donut, rings), floor plans, heat maps, and logos are hand-authored **inline SVG**
- Interactivity where needed (tabs, matrix selection, modals) is small vanilla JS embedded per page

---

## 2. Screen Inventory

### 2.1 Contractor Module

| File | Title | Summary |
|------|-------|---------|
| `marketplace.html` | Contractors & DLOs | Contractor marketplace / directory with trade filter bar (14+ categories) |
| `contractor-onboarding.html` | Contractor Onboarding | Multi-step wizard with clickable stepper; contractor type selector (Sole Trader vs Organisation) with conditional fields; business documents; trade type dropdown; Key Personnel cards with per-person certifications, accreditations and insurance (multi-entry uploads, predefined dropdowns + "Other/Custom"); H&S compliance document table with expiry tracking |
| `contractor-profile.html` | MJ Mechanical Ltd | Comprehensive contractor profile with 9 populated tabs, Organisation badge, Key Personnel tab, live location & geo-tracking map tab (fullscreen + ETA countdown), QR verification modal, Voice/Message/Video contact options, certificates viewer |
| `contractor-profile-v1.html` | Contractor Profile (v1) | Earlier profile version retained for reference |
| `contractor-jobs.html` | Job History — MJ Mechanical Ltd | Contractor job history board |

### 2.2 Risk Management

| File | Title | Summary |
|------|-------|---------|
| `add-risk.html` | Add New Risk | 6-section risk form; interactive 5×5 likelihood/severity matrix that highlights the computed cell; right panel with risk summary, guidance and categories |
| `add-control.html` | Add Control / Mitigation | Dark-shell 7-section form; tag chips; linked remedial actions; right panel with mitigation summary, control categories and a 5-step approval workflow (Draft → Submitted → Under Review → Approved → Implemented) |

### 2.3 Building-Level Compliance

| File | Title | Summary |
|------|-------|---------|
| `compliance-register.html` | Compliance Register | Riverside House dashboard: 6 KPI cards, RAG overview donut, compliance-by-category bars, review timeline, 10-row requirements register with evidence bars, evidence gaps, **Top Compliance Risks 5×4 gradient heat map** with risk-area pills, and a fixed AI Assistant rail (quick actions, standards overview, action status donut, recent activity) |
| `building-safety-cases.html` | Building Safety Case — Riverside House | Building safety case management |

### 2.4 Property-Level Safety Dashboards (Flat 12, Oak Court)

All eight share a common shell: **dark navy sidebar** (`#0d1e4a`) with contextual submenu, **breadcrumb topbar** (64px, ⌘K search, notifications, user), **property header card** (photo, tags, action buttons), **KPI row** (8–9 cards), **register + timeline row**, **analysis panel rows**, and a **292px right rail** (AI Assistant quick actions, readiness donut, alerts & flags, snapshot tiles, evidence & documentation bars).

| File | Title | Distinctive content |
|------|-------|---------------------|
| `repairs-compliance.html` | Repairs Compliance | Work-order register (WO-…), repair status timeline, linked cases, contractor allocation & performance with star ratings, repairs age donut, recent completions, appointments, completion certificates, resident access outcomes, repeat-repair root causes |
| `smoke-heat-alarms.html` | Smoke & Heat Alarms | Detector register (sensor type, power source, next due), alarm test timeline, **device coverage floor plan** (SVG, smoke/heat markers), testing & resident engagement, faults, replacement schedule, 183-day due ring |
| `gas-safety.html` | Gas Safety | Tab strip (12 tabs, Gas Safety active); CP12 lifecycle — gas safety register (boiler/hob/meter/flue/CO alarm), certificate & inspection timeline with **No Access** badge, appliances & asset details, access & engagement (vulnerability, contact preference), gas risks, 365-day CP12 SLA clock |
| `electrical.html` | Electrical | EICR register (consumer unit, circuits), inspection timeline, **C1/C2/C3/FI observation code chips**, circuit & asset details (RCD/SPD/earthing), resident access, electrical risks, EICR SLA clock |
| `fire-safety.html` | Fire Safety | Fire-specific sidebar submenu; fire safety register (door set, self-closer, intumescent strips, fire stopping, escape route, signage), inspection timeline, **door set & compartmentation spec sheet**, defects, resident access/visits, means-of-escape checklist (6 × Pass), 91-day SLA ring |
| `hhsrs.html` | HHSRS | Hazard register with A–D **band chips**, **5×5 hazard matrix** (green→red, highlighted score cells, band legend), priority hazards donut (Cat 1/2/3), assessment history, mitigation & action tracker, assessor notes, evidence completeness by assessment type, upcoming reviews |
| `damp-mould.html` | Damp & Mould | Case register (DM-…), **root cause & affected-areas floor plan** (impact shading), **moisture/humidity trend line chart** (7D/30D/90D), inspection & remediation timeline, resident vulnerability & health impact, remedial actions, contractor schedule, evidence tiles, compliance clock + SLA breach donuts |
| `epc-energy.html` | EPC / Energy | Energy-specific sidebar submenu; EPC rating C (SAP 72 → target B), energy efficiency register with rating chips, EPC assessment timeline, energy performance summary (U-value / efficiency / lighting with Fair/Good badges), improvement measures (SAP uplift + cost), retrofit priorities, **projected savings & carbon reduction chart** (cost bars + carbon line, −27%) |

### 2.5 Portfolio-Level Programme

| File | Title | Summary |
|------|-------|---------|
| `gas-compliance.html` | Gas Compliance | North Region Housing Association (10,000 properties, 185 estates, 12 LAs): org header with property-type mix and bulk actions; 9 KPIs; **completed-vs-due 12-month bar chart** with overdue trend line; compliance status mix donut; overdue-by-days ageing bars; alerts & urgent items; **17-column Gas Programme Register** (fixed-layout, horizontally scrollable, filters, saved views, pagination 1–400); escalation ladder (Manager 7d / Director 14d / Legal 28d+); quick actions grid; programme snapshot |

---

## 3. Design System

### 3.1 Tokens

Defined in each file's `:root`:

| Token | Value | Use |
|-------|-------|-----|
| `--accent` | `#1754d8` | Primary blue — buttons, links, active nav, In Progress |
| `--accent-h` | `#1247b8` | Button hover |
| `--green` | `#16a34a` | Compliant / Pass / Complete |
| `--amber` | `#d97706` | At Risk / Partial / Medium |
| `--red` | `#dc2626` | Overdue / Non-Compliant / High |
| `--purple` | `#7c3aed` | No Access / Monitoring |
| `--nav` | `#0d1e4a` | Dark navy sidebar (property/portfolio shell) |
| `--bg` | `#f4f5f7` | Page background |
| `--panel` | `#ffffff` | Card surface |
| `--g1`…`--g12` | gray ramp | Text, borders, muted surfaces |

Each status color has a 10%-alpha companion (`--green-a`, `--amber-a`, `--red-a`, `--accent-a`) used as badge/tile backgrounds.

Typography: **Inter** 400–800. Base size 13px; tables run 9.5–11px; KPI values 18–24px bold.

### 3.2 Layout shell

```
┌──────────┬───────────────────────────────────────────────┐
│          │ topbar 64px — title + breadcrumb | ⌘K search  │
│ sidebar  ├──────────────────────────────┬────────────────┤
│ 200px    │ main column                  │ right rail     │
│ dark     │ (header card, KPI row,       │ 292px          │
│ navy     │  registers, panels…)         │ (AI, donuts,   │
│          │                              │  alerts, snap) │
└──────────┴──────────────────────────────┴────────────────┘
```

- Grid: `.content { grid-template-columns: minmax(0,1fr) 292px }` — the `minmax(0,…)` is required so wide tables can shrink/scroll instead of overflowing into the rail
- Wide registers use `table-layout: fixed` + `<colgroup>` widths inside an `overflow-x:auto` wrapper with a styled scrollbar

### 3.3 Recurring components

| Component | Pattern |
|-----------|---------|
| **KPI card** | icon tile (28–34px, tinted bg) + small label, large value, sub-label/trend (`↑/↓ n vs last 30 days`) |
| **Status badge** | 9–10px, 600 weight, pill radius, tinted background (`Compliant`, `At Risk`, `Overdue`, `High/Medium/Low`, `Access Granted/Denied`) |
| **Register table** | compact th 9–10px gray, striped hover, kebab/eye/link actions |
| **Timeline** | dashed vertical connector (`::before`) + colored circular status icons, timestamp / bold title / gray detail |
| **Donut / ring** | SVG circles with `stroke-dasharray`/`stroke-dashoffset`, center value + label, right-hand dot legend |
| **Heat map / matrix** | flex-row cells with per-cell background, axis labels, band legend, ring-highlighted cells |
| **Evidence bars** | label + `n / m` count + green progress track + % |
| **Right-rail AI Assistant** | BETA chip + 5–6 bordered quick-action buttons |
| **Snapshot tiles** | 3-per-row bordered mini-tiles with icon, value, caption |
| **Floor plan** | SVG walls/door-gaps, device markers or impact shading |

---

## 4. Demo Entities

All data is fictional:

- **Buildings/properties**: Riverside House (Manchester, 18 storeys, 128 units) · Flat 12, Oak Court (Oak Road, Manchester M4 5GH)
- **Organisation**: North Region Housing Association (10,000 properties)
- **People**: Sarah Johnson (Building Safety / Compliance Manager) · Tom Richards · James Whitfield · James Cartwright · Mark Davies (Elmhurst) · Jordan Patel · Sarah Mitchell
- **Contractors**: MJ Mechanical Ltd · Gas Safe NW Ltd · Northern Elec Ltd · Fire Safe NW Ltd · FlowFix Ltd · BrightSpark Ltd · ClearView Glazing · EnviroVent Ltd · FixRight Joinery · DampCare Solutions Ltd · Mitie · PHS Group · Northern Gas Care · City Technical
- **References**: CP12-565784 · EICR-527894 · WO-25xx work orders · DM-100xx damp cases · NRHA000123xx UPRNs · CASE-1xxx / CERT-5xxx

---

## 5. Development

### Running locally

```bash
npx http-server . --cors -c-1
# open http://localhost:8080/<page>.html
```

A preview launch config exists at `.claude/launch.json` (not committed).

### Conventions

- One screen = one file; copy the closest existing shell when adding a screen
- Keep all styles in the page `<style>` block using the shared tokens
- New icons: 12–14px inline SVG, `stroke="currentColor"`, stroke-width ≈ 1.2–1.4
- Registers that exceed the column width: give the grid track `minmax(0,1fr)`, the table `table-layout:fixed` + `<colgroup>`, and let long text cells wrap

---

## 6. Development History

Condensed from the git log, oldest first.

### Phase 1 — Foundation & Contractor module
- Initial platform UI (`marketplace`, contractor pages)
- Contractor profile built out to 9 fully-populated tabs: photo, QR verification modal, reference number, live location & geo-tracking map (dedicated tab, fullscreen, ETA countdown), Voice/Message/Video contact, certificates viewer, No. of Employees stat, expanded trade filters
- Contractor onboarding: clickable stepper, certificate uploads, contractor type selector (Sole Trader vs Organisation) with conditional fields, Key Personnel management (card layout → 8-column table), multi-entry certifications/accreditations/insurance with dropdown suggestions + custom option, H&S compliance document table with expiry tracking
- `contractor-jobs` page; previous profile retained as `contractor-profile-v1`

### Phase 2 — Compliance & property safety dashboards
- **Risk management**: `add-risk` (interactive 5×5 matrix) and `add-control` (approval workflow)
- **Building level**: `compliance-register` (KPIs, RAG donut, category bars, review timeline, register, gradient risk heat map, AI rail) and `building-safety-cases`
- **Property level (Flat 12, Oak Court)**: `repairs-compliance`, `smoke-heat-alarms`, `gas-safety`, `electrical`, `hhsrs`, `damp-mould`, `fire-safety`, `epc-energy` — establishing the shared dark-navy shell, tab strip, timelines, SLA rings, floor plans, and hazard matrix
- **Portfolio level**: `gas-compliance` — 10,000-property gas programme with 17-column register; register later reworked to fixed column widths + horizontal scroll to eliminate text overlap
- Project documentation: `README.md`, `PROJECT.md`

---

*SafeBuild Cloud © 2025 — prototype/demo. All names, addresses and certificate numbers are fictional.*
