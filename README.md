# Spiro KYC V2 — Interactive Prototype

A self-contained, front-end-only prototype of the V2 KYC flow for Spiro's asset-financing product. Built from the *Asset Financing — PRDs* document to align stakeholders before engineering build-out.

**Live demo:** _add your GitHub Pages URL here after enabling Pages_

---

## What's in the prototype

A single page with three top-nav entry points:

| Section | Audience | Contents |
|---|---|---|
| **Overview** | Anyone | End-to-end flow at a glance, role map, design principles |
| **Internal Portal** | Spiro & Financier teams | Role-based sidebar (Swap Agent · Spiro Ops · Financier Admin · Compliance / Legal) with 21 sub-views |
| **Rider experience** | End customer (boda-boda rider) | SMS thread, in-app status, under-review and declined states |

### Roles in the Internal Portal

- **Swap Agent** — Dashboard, New lead, CX data form, KYC verification, My applications, Mobile preview
- **Spiro Ops** — Review queue, Case detail, Webhook failures, Geo-risk heat map, ML model health
- **Financier Admin** — Identity & KYC config, Risk & decisioning, Roles & approvals, Webhook config, Change history
- **Compliance / Legal** — Audit log, Consent tracking, ML bias audit, Data residency, Retention policy

### Form validation

The **New lead** and **CX data form** views run real regex validation on every keystroke:

| Field | Rule |
|---|---|
| Full name | `/^[A-Za-z][A-Za-z'\- ]{1,49}$/` |
| Phone (UG) | `/^\+?256[\s-]?7\d{2}[\s-]?\d{3}[\s-]?\d{3}$/` |
| Phone (UG/KE/RW) | `/^\+?(256\|254\|250)[\s-]?\d{9}$/` |
| NIN | `/^[A-Z]{2}[0-9A-Z]{12}$/` |
| Date of birth | `DD / MM / YYYY` · `19xx` or `20xx` |
| Monthly income | numeric + commas, min UGX 100,000 |
| Driving permit | `/^[A-Z]{2}\d{6,10}$/` |

Submit buttons stay disabled until every field passes.

---

## Brand guidelines applied

- **Primary green:** `#00875A` (with darker `#0A5A3D` and light tint `#E6F4EE`)
- **Typography:** Poppins (headings) + Lato (body) — per spironet.com
- Consistent type scale (12–32px tokens), spacing, and component sizing across all views

---

## Running locally

It's a single static HTML file. Either:

1. **Open the file directly** — double-click `index.html` (works in any modern browser)
2. **Serve with a simple HTTP server** —
   ```bash
   python3 -m http.server 8000
   # then visit http://localhost:8000
   ```

No build step, no dependencies, no API calls. All data is illustrative.

---

## Source

Built from `Asset Financing — PRDs.pdf` covering:

- Context & problem statement (V0 → V2)
- User personas, onboarding flow, decision gates
- Detailed feature requirements (Modules A–F)
- Financier configuration layer + admin panel roles
- A/B testing strategy, risks & mitigations, dependencies

---

_Prototype scope: front-end only — no real API calls, no backend. Designed for stakeholder demos and PRD alignment._
