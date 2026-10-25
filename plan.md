# Implementation Plan

## 1. Scope and decisions

Implement only the evaluated deliverable: one static, responsive dashboard page using semantic HTML and Tailwind CSS v4. The page is backed by the prepared sample CSV at `data/sample-data.csv`; its values are transcribed into static HTML and reconciled with the CSV because project-authored JavaScript is prohibited.

In scope:

- A single root `index.html` served by the existing Flask starter server.
- At least three KPI cards, at least three driver views, and an operational table or list, in that order.
- Mobile-first layouts using Tailwind `sm:`, `md:`, and `lg:` variants.
- Clearly disclosed sample dataset, reporting period, definitions for displayed rates, and missing ad-cost/ROI limitation.
- If useful, a small static note that platform connections are planned/not connected.

Out of scope: live platform connectors, JavaScript/data loading, interactivity, authentication, backend/API work, storage, chart libraries, photo assets, and production analytics. Do not add UI controls that imply these capabilities work.

## 2. Page structure

Use one `index.html` with:

- Document metadata (`charset`, viewport, descriptive title) and the exact Tailwind CSS v4 browser CDN snippet from `spec.md`.
- A semantic `<header>` with the dashboard name and a visible sample-data/report-period disclosure.
- A `<main>` with one page-level heading and three ordered `<section>` elements:
  1. **Outcome KPIs:** at least three consistent cards.
  2. **Performance drivers:** at least three clearly titled comparison or explanatory widgets.
  3. **Operational details:** at least one semantic table or list.
- Optional footer/notes for metric definitions, sample-data caveat, or connector roadmap. Add navigation only if it leads somewhere meaningful.

## 3. Data presentation

- Treat `data/sample-data.csv` as the canonical prepared input; do not invent unrelated values in the HTML.
- Display the reporting period and a conspicuous “Sample data” indicator.
- Calculate totals/derived amounts consistently from the CSV. Product commissions must follow 15% of price.
- Define any displayed engagement/conversion rate and denominator nearby. Aggregated rates should be calculated from summed numerators/denominators, not by averaging row percentages.
- Advertising cost is unknown (blank in the CSV). Do not convert blank cost to zero or claim a factual ROI.
- Make no claim that data is live or that a platform account is connected. Any connector reference is an informational, noninteractive placeholder only.
- Keep details simple enough to verify manually; no runtime data transformation is introduced.

## 4. Responsive and visual implementation

- Begin with a narrow, single-column phone layout; retain the KPI → drivers → operational sequence at all widths.
- Apply `sm:`, `md:`, and `lg:` responsive variants to adapt spacing, grid columns, and widget/table presentation.
- Prevent page-level horizontal scrolling. On small screens, simplify table columns or contain horizontal overflow within the table region only when necessary.
- Use semantic, readable labels, consistent cards, visible focus for any real links, and sufficient contrast. Color must not be the only way a metric is communicated.
- Use Tailwind utilities only. No custom CSS is expected; only add narrowly scoped CSS if a CSS-only visualization cannot reasonably be expressed with utilities.
- No photos, image folder, icon package, chart package, or other dependency is required.

## 5. Delivery sequence

Follow `tasks.md`: inspect the starter, verify the prepared CSV, build semantic page structure, add KPI and driver content, add operational details/disclosures, make it responsive, then perform final compliance checks. Keep task status accurate; do not mark viewport/browser checks complete unless performed.

## 6. Verification approach

- Inspect HTML for semantic landmarks, heading hierarchy, three ordered blocks, at least 3 KPIs, at least 3 drivers, and an operational table/list.
- Verify values and data disclosures against `context.md` and `data-contract.md`; re-compute displayed aggregates from `data/sample-data.csv`.
- Confirm the exact Tailwind v4 browser CDN is used and no active prohibited technology or data-loading script appears.
- Serve using the existing `python3 server.py` setup and inspect narrow phone, tablet, and desktop viewports. Check responsive reflow, page-level overflow, readability, and table behavior.
- State which checks were done and which could not be performed. Do not claim live integration or production analytics verification.
