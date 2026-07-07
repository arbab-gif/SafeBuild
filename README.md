# SafeBuild Cloud

**Building Safety Platform** — high-fidelity HTML prototypes for a UK building safety and compliance management SaaS.

SafeBuild Cloud covers the full building safety lifecycle for housing providers: compliance registers, risk management, contractor management, property-level safety dashboards (gas, electrical, fire, damp & mould, HHSRS, EPC), and portfolio-wide compliance programmes.

## Tech Stack

- **Plain HTML / CSS / SVG** — every screen is a single self-contained `.html` file
- No frameworks, no build step, no JavaScript dependencies
- [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts
- Charts, donuts, floor plans, and illustrations are hand-built inline SVG

## Getting Started

Serve the folder with any static file server and open a page in the browser:

```bash
npx http-server . --cors -c-1
# then open e.g. http://localhost:8080/compliance-register.html
```

Or simply open any `.html` file directly in a browser — no server required.

## Screens

### Compliance & Registers

| Page | Description |
|------|-------------|
| [compliance-register.html](compliance-register.html) | Building-level compliance dashboard — KPI cards, RAG overview, category bars, review timeline, requirements table, evidence gaps, risk heat map, AI assistant panel |
| [gas-compliance.html](gas-compliance.html) | Portfolio-level gas programme (10,000 properties) — completed-vs-due chart, status mix, overdue ageing, 17-column programme register with filters, escalations and quick actions |
| [building-safety-cases.html](building-safety-cases.html) | Building safety case management |

### Property Compliance (Flat 12, Oak Court)

Property-level dashboards sharing a common shell — dark navy sidebar, breadcrumb topbar, property header, KPI row, register + timeline, analysis panels, and a right rail (AI assistant, readiness donut, alerts & flags, snapshot, evidence).

| Page | Description |
|------|-------------|
| [repairs-compliance.html](repairs-compliance.html) | Repairs & work orders — register, repair timeline, contractor performance, age analysis, appointments, certificates, resident access outcomes |
| [smoke-heat-alarms.html](smoke-heat-alarms.html) | Detector register, alarm test timeline, device coverage floor plan, testing & resident engagement, replacement schedule, due-date ring |
| [gas-safety.html](gas-safety.html) | CP12 lifecycle — gas safety register, certificate & inspection timeline, appliances & asset details, access & engagement, SLA clock |
| [electrical.html](electrical.html) | EICR management — electrical safety register, inspection timeline, C1/C2/C3/FI observation codes, circuit & asset details, risks |
| [fire-safety.html](fire-safety.html) | Fire door & compartmentation detail, defects, means of escape checklist, resident access, inspection timeline |
| [hhsrs.html](hhsrs.html) | HHSRS hazard register, 5×5 risk score matrix with band legend, priority hazards donut, mitigation tracker, assessor notes |
| [damp-mould.html](damp-mould.html) | Case register, root cause & affected areas floor plan, moisture/humidity trend chart, vulnerability & health impact, remedial actions, SLA clocks |
| [epc-energy.html](epc-energy.html) | EPC rating & SAP score, energy efficiency register, performance summary, improvement measures, projected savings & carbon reduction chart |

### Risk Management

| Page | Description |
|------|-------------|
| [add-risk.html](add-risk.html) | Add New Risk form — 6 sections with an interactive 5×5 likelihood/severity matrix |
| [add-control.html](add-control.html) | Add Control / Mitigation form — 7 sections, linked risk summary, approval workflow |

### Contractor Management

| Page | Description |
|------|-------------|
| [contractor-onboarding.html](contractor-onboarding.html) | Contractor onboarding with conditional sole trader/organisation fields, key personnel, H&S document tracking |
| [contractor-profile.html](contractor-profile.html) | Contractor profile |
| [contractor-jobs.html](contractor-jobs.html) | Contractor jobs board |
| [marketplace.html](marketplace.html) | Contractor marketplace |

## Design System

All pages share a common set of design tokens (defined in each file's `:root`):

| Token | Value | Use |
|-------|-------|-----|
| `--accent` | `#1754d8` | Primary blue — buttons, links, active nav |
| `--green` | `#16a34a` | Compliant / pass / positive |
| `--amber` | `#d97706` | At risk / partial / warning |
| `--red` | `#dc2626` | Overdue / non-compliant / high severity |
| `--nav` | `#0d1e4a` | Dark navy sidebar |
| `--bg` | `#f4f5f7` | Page background |
| `--g1`–`--g12` | gray scale | Text, borders, surfaces |

Recurring patterns:

- **Layout** — fixed 200px dark sidebar, fixed 64px white topbar with breadcrumb, scrollable main column, 292px right rail
- **KPI cards** — icon tile, label, large value, sub-label trend
- **Registers** — compact tables with colored status/severity badges, kebab actions
- **Timelines** — dashed vertical connector with colored status icons
- **Donuts / rings** — multi-segment SVG `stroke-dasharray` charts with center labels
- **Right rail** — AI Assistant quick actions, readiness donut, alerts & flags, property snapshot tiles, evidence progress bars

## Demo Data

All content is fictional demo data (properties, residents, contractors, and certificates such as *Flat 12, Oak Court* and *North Region Housing Association*).
