# AdaB Health — Pitch / Program Overview Dashboard

> _Recovery is personal. Care should be too._

A **standalone, single-screen executive dashboard** for demoing the AdaB Health
platform to partners (GPHA Philadelphia, Rescue Mission Trenton). It shows
enrollment, outcomes, peer fidelity, street-medicine outreach, and resource
capacity at a glance — using **illustrative sample data**, so it's safe and
reliable to present with no login and no live backend.

## Why it's a separate project

This repo is **deliberately isolated** from the main AdaB Health app. It shares
no code, no server, and no data with the live demo — so you can freely iterate on
the pitch here without any risk of breaking the working demo environment. It's a
zero-dependency static site: `node server.js` (or Replit **Run**) just works, no
`npm install` required.

## Run it

**Locally**
```bash
npm start          # → http://localhost:3000
# or, no package manager at all:
node server.js
```

**On Replit** — import this repo into a new Repl and press **Run** (or **Deploy**
to publish it). Nothing here touches the main app's Repl.

## Present it

- Open the page and **present full-screen**. It's responsive (looks right on a
  laptop or projector) and has a **light/dark toggle** (top-right ◐ Theme) for the
  room you're in.
- Hover the acuity trend line for per-month values.
- Everything is one scroll — KPIs up top, then engagement, outcomes, workforce,
  outreach, capacity, and an impact snapshot.

## Customize the sample data

All numbers live in **one place** — the `DATA` object near the top of the
`<script>` in `index.html`. Edit values there and refresh; every tile and chart
re-renders from it. No build step.

```js
const DATA = {
  kpis:   [ { value:'1,284', label:'Patients enrolled', delta:'▲ 18% YoY', good:true }, … ],
  funnel: [ { stage:'Enrolled', n:1284 }, … ],
  acuity: [ ['Jan',10.4], ['Feb',9.9], … ],   // avg acuity index over time (lower = better)
  triage: [ ['Low',596,'low'], ['Moderate',476,'mod'], ['High',412,'high'] ],
  peers:  [ ['M. Alvarez',88], … ],           // Peer Fidelity Score; ≥80 shows an "AdaB Certified" badge
  street: { encounters:342, referrals:214, followups:118 },
  capacity: [ ['Clinicians',38,45], … ],      // [name, used, capacity]
  impact: [ ['months → same week', 'Wait to first contact…'], … ]
};
```

## Design notes

- Brand-cohesive with the main app (calm teal palette, serif headings, layered
  depth, light + dark).
- Charts follow a validated data-viz method: single-hue magnitude bars, a status
  triple (low/moderate/high) that's **colorblind-safe and always labeled**, thin
  marks with rounded ends, recessive gridlines, and hover tooltips on the trend.

> **Illustrative sample data — not a live feed or real patient records.**
> AdaB Health is a reflective care-navigation tool, not a diagnostic instrument.
