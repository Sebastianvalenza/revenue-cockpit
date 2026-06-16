# Revenue Cockpit

A single-screen control surface for a sales director running multiple regions. It answers the question that governs the quarter — *are we going to make the number, and which region is putting it at risk?* — by pulling attainment, manager performance, pipeline health and the end-of-quarter forecast onto one screen.

**[Live demo](https://sebastianvalenza.github.io/revenue-cockpit/)** · runs instantly on synthetic data, or drop in your own CRM export.

---

## The problem it solves

A director with four regional managers doesn't read deal logs — they read risk. But the answer to *will we hit quota?* is normally scattered across a region scorecard, four managers' spreadsheets, a pipeline report and a forecast deck, each built on slightly different definitions. Comparing managers fairly is nearly impossible when everyone reports their own way.

Revenue Cockpit puts the four regions on one yardstick and turns four reports into one decision surface — moving from *what closed* (attainment, manager metrics) to *what will happen* (pipeline coverage, forecast).

## What's inside

- **Attainment** — closed-won vs quota by region and consolidated, each bar measured against its own quota marker. The headline question — do we make the number? — answered in five seconds, with the at-risk region obvious before any other tab is read.
- **By region** — the four regions and their managers on the same four metrics: attainment, win-rate, sales cycle and average deal. The same yardstick for everyone makes the comparison honest — a low win-rate with a long cycle is a closing problem, not a pipeline-volume one, and the screen makes that diagnosable.
- **Pipeline** — open value by stage, pipeline coverage against the gap to quota (healthy is 3–4×), and the stalled deals dragging the quarter. The stalled value usually concentrates in the same region failing attainment — pipeline confirms the diagnosis.
- **Forecast** — cumulative bookings to quarter-end with a commit / best-case / worst-case band against the quota line. The number the director takes to the board, with the honest uncertainty shown as the gap between the lines rather than one false-precise figure.

## Use your own data

The cockpit ships with a deterministic synthetic quarter (four regions, ~€12M quota, week 9 of 13) so it runs the moment it loads. The **Upload CSV** button accepts a deals/opportunities export from any CRM — it auto-detects account, amount and stage columns, lets you map the rest, and recomputes attainment, pipeline and forecast on your own deals. It handles comma, semicolon and tab separators, UTF-8 (with or without BOM) and Latin-1 encodings, and European or US number formats — so a `1.250.000,00` deal value reads as €1.25M, not €1.25 — reporting any rows it has to skip rather than dropping them silently. Nothing leaves the browser.

## Wired into the ecosystem

Revenue Cockpit sits between the retained base and the cash, and connects to both sides:

- **↑ From Customer Cockpit.** The base the [Customer Cockpit](https://github.com/sebastianvalenza/customer-cockpit) retains and expands is the installed revenue new deals build on — net-new is added on top of what's already kept, not counted in isolation.
- **↓ Into AR Cockpit.** The **↓ Won deals → AR** button exports this quarter's closed-won deals as an invoice-shaped file; upload it into the [AR Cockpit](https://github.com/sebastianvalenza/ar-cockpit) and the same money appears as a receivable to collect — the deal a region books becomes the cash the next tool chases.

## Part of an operations ecosystem

Revenue Cockpit is one of five control surfaces for a single multi-hub operation, built to follow one decision down the whole chain — *from the shift being covered to the cash being collected*:

| Stage | Tool | The question it answers |
|---|---|---|
| Capacity | [Shift Planner](https://github.com/sebastianvalenza/shift-planner) | Is the shift covered? |
| Workflow | [Ticket Triage](https://github.com/sebastianvalenza/ticket-triage) | Who takes what, without collisions? |
| Productivity | [Performance Tracker](https://github.com/sebastianvalenza/performance-tracker) | Is the team performing? |
| Retention | [Customer Cockpit](https://github.com/sebastianvalenza/customer-cockpit) | Does the base retain and grow? |
| **Revenue** | **Revenue Cockpit** *(this tool)* | **Are we going to make the number?** |
| Cash | [AR Cockpit](https://github.com/sebastianvalenza/ar-cockpit) | Did the money actually land? |

All six run on the same four hubs (Madrid 🇪🇸 · Berlin 🇩🇪 · Warsaw 🇵🇱 · Dublin 🇮🇪), the same ten markets, the same seed and the same visual system — one company seen from six functions. The hubs are the same operating centres throughout: here they are the sales regions whose deals this cockpit forecasts, and in the support tools they are the floors whose agents get staffed, triaged and scored. The deal a region books here becomes the receivable the [AR Cockpit](https://github.com/sebastianvalenza/ar-cockpit) collects — closing the loop from booked revenue to landed cash. Same world, different layer of the business.

## Stack

Single-file `index.html` — no backend, no build step, no framework — deployable to GitHub Pages as-is. Vanilla JavaScript for the data model and forecast logic, Chart.js for the forecast chart, PapaParse for CSV import. Synthetic data is generated from a fixed seed (`mulberry32`) so the quarter is identical on every load. Dark and light themes, persisted locally. Fully client-side — no credentials, no data leaving the page.

## Notes

All data is synthetic. No real customers, deals or company names appear anywhere in this repository. Account names, regions, quotas and figures are randomly generated for demonstration.

---

*[linkedin.com/in/sebastianvalenza](https://linkedin.com/in/sebastianvalenza)*
