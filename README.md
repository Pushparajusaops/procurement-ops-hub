# B2B Shipment Performance Dashboard

A single-file HTML dashboard for tracking B2B shipment performance across Dubai and Saudi lanes, built for weekly procurement reviews. It reports SLA compliance, turnaround time (TAT), and delivery volume for Shipglobal, Boxit, and Fedex.

## What it shows

- **KPI summary** — delivered volume, SLA compliance, average TAT, breaches, and active in-transit count.
- **SLA compliance by courier and lane** — on-time rate against each courier/destination target.
- **Average TAT by courier** — calendar days from label creation to delivery.
- **Weekly delivery volume and SLA breaches** — trend over the last 16 weeks.
- **Shipment detail table** — sortable, filterable, exportable.

## Filters

Date basis (delivery date or label date), from/to range, courier, destination, SLA result (within/breached), and quick ranges (7/30/90 days, month to date).

## Export

Both **Export** buttons download the currently filtered rows as a CSV, named by courier/lane/date, ready to send to a courier partner.

## SLA rules

TAT for SLA is measured in **working days** from label creation to delivery, excluding each office's weekly closure:

- Dubai office closed Sundays
- Saudi office closed Fridays

Targets:

| Courier    | Lane  | Target |
|------------|-------|--------|
| Shipglobal | Dubai | 3 days |
| Shipglobal | Saudi | 4 days |
| Boxit4me   | Dubai | 2 days |

Other courier/lane combinations use editable default targets. All targets live in the `SLA` object near the top of the script inside `index.html`.

## Live data

The dashboard opens on an embedded snapshot and attempts to fetch the live Google Sheet on load and on **Refresh**. For the live fetch to work, the sheet must be readable without login:

1. In the sheet: **Share → General access → Anyone with the link → Viewer**, or
2. **File → Share → Publish to web** → publish the `B2B Tracking` tab as CSV.

The source badge shows **Live** (green) when the sheet is reachable and **Snapshot** (amber) when it falls back to embedded data.

To point at a different sheet or tab, edit `SHEET_ID` and `SHEET_GID` near the top of the script in `index.html`.

## Hosting

The dashboard is a single self-contained file. Open `index.html` in any browser, or host it with GitHub Pages (see repo settings) to share a link with your team.

## Local use

No build step, no dependencies. Download `index.html` and open it.
