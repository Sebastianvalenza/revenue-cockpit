# Customer Cockpit

The bridge from support quality to retained revenue. It turns a flat book of customer accounts into the read a retention lead acts on: what the net revenue retention actually is, which accounts are healthy and which are leaking, where the base is expanding, and where churn concentrates — with account health driven by how well the support floor is performing.

**[Live demo](https://sebastianvalenza.github.io/customer-cockpit/)** · runs instantly on synthetic data, or drop in your own account book.

---

## The problem it solves

In a recurring-revenue business, most of next year's revenue is already in the building — it's the base you keep and grow, not the deals you haven't closed yet. But that base is read in fragments: a churn report here, an NRR slide there, a health-score spreadsheet a CSM keeps by hand, none of them tied to *why* an account stays or leaves. And the strongest driver of whether an account renews — how well support actually served it — usually lives in a different team's dashboard entirely, never connected to the revenue it moves.

Customer Cockpit puts retention on one screen and makes that connection explicit. Net revenue retention is the headline; underneath, account health is seeded by each hub's support quality, so the region with the weakest support floor carries the worst retention — visible in a single health-versus-revenue chart. It answers the question the base poses every quarter — *does what we already won retain and grow?* — and shows the support-quality lever that moves the answer.

## What's inside

- **Retention** — the headline. Net Revenue Retention (NRR) as the lead figure, with Gross Retention (GRR) beside it, and an ARR bridge that walks starting ARR through expansion, contraction and churn to the ending number. NRR above 100% means the base grows on its own before a single new deal is added; the bridge shows exactly where it's won or lost.
- **Health & Risk** — the support→revenue link made visible. The book split into healthy / watch / at-risk by health score, ARR at risk quantified, and a scatter of account health against retained ARR — the one chart that shows support quality and money are the same story. Average health by region is fed directly by support QA.
- **Expansion** — upsell and cross-sell on the installed base: expansion ARR, net revenue change, and the top expanding accounts. The cheapest revenue there is — it grows the base before new sales add anything.
- **Churn & Cohorts** — where revenue leaks: churned ARR, the largest lost accounts, and gross retention by signup cohort, so a base that loses its older customers is distinguishable from one that loses new ones.

Retention math is the standard set: `NRR = (starting ARR + expansion − contraction − churn) / starting ARR`, with GRR excluding expansion credit. Account health is a 0–100 score; accounts resolve to retained, expanded, contracted or churned each period.

## Use your own data

The cockpit ships with a deterministic synthetic book (~250 accounts, ~€23M ARR, across four hubs and ten markets) so it runs the moment it loads. The **Upload CSV** button accepts an account export from any CRM or customer-success system — it auto-detects account, ARR, health, region and cohort columns, lets you map the rest, and derives retention status when it isn't given. It handles comma, semicolon and tab separators, UTF-8 (with or without BOM) and Latin-1 encodings, and European or US number formats — so a `1.250.000,00` ARR reads as €1.25M — reporting any rows it has to skip rather than dropping them silently. Nothing leaves the browser.

## Wired into the ecosystem

Customer Cockpit is the link that connects the support tools to the finance tools — and it carries data both ways:

- **↑ From Performance Tracker.** Export QA-by-operation from the [Performance Tracker](https://github.com/sebastianvalenza/performance-tracker) and import it here: account health re-scores from your real support quality, so the support floor's performance drives the retention read instead of a synthetic assumption.
- **↓ Into Revenue Cockpit.** Export the retained and expanded base as an installed-revenue file the [Revenue Cockpit](https://github.com/sebastianvalenza/revenue-cockpit) builds on — the revenue you keep is the foundation new deals are added to, not a separate number.

## Part of an operations ecosystem

Customer Cockpit is one of six control surfaces for a single multi-hub operation, built to follow one decision down the whole chain — *from the shift being covered to the cash being collected*. It is the hinge: where operational quality becomes retained revenue.

| Stage | Tool | The question it answers |
|---|---|---|
| Capacity | [Shift Planner](https://github.com/sebastianvalenza/shift-planner) | Is the shift covered? |
| Workflow | [Ticket Triage](https://github.com/sebastianvalenza/ticket-triage) | Who takes what, without collisions? |
| Productivity | [Performance Tracker](https://github.com/sebastianvalenza/performance-tracker) | Is the team performing? |
| **Retention** | **Customer Cockpit** *(this tool)* | **Does the base retain and grow?** |
| Revenue | [Revenue Cockpit](https://github.com/sebastianvalenza/revenue-cockpit) | Are we going to make the number? |
| Cash | [AR Cockpit](https://github.com/sebastianvalenza/ar-cockpit) | Did the money actually land? |

All six run on the same four hubs (Madrid 🇪🇸 · Berlin 🇩🇪 · Warsaw 🇵🇱 · Dublin 🇮🇪), the same ten markets, the same seed and the same visual system — one company seen from six functions. The hubs are the same operating centres throughout: the support floor the Performance Tracker scores is the floor whose quality drives the health of the accounts this cockpit retains, and the base it retains is the revenue the Revenue Cockpit builds on. Same world, different layer of the business.

## Stack

Single-file `index.html` — no backend, no build step, no framework — deployable to GitHub Pages as-is. Vanilla JavaScript for the retention model and the health-scoring logic, Chart.js for the bridge, scatter and cohort visualizations, PapaParse for CSV import. Synthetic data is generated from a fixed seed (`mulberry32`) so the book is identical on every load. Dark and light themes, persisted locally. Fully client-side — no credentials, no data leaving the page.

## Notes

All data is synthetic. No real customers, accounts or company names appear anywhere in this repository. Account names, markets and figures are randomly generated for demonstration.

---

*[linkedin.com/in/sebastianvalenza](https://linkedin.com/in/sebastianvalenza)*
