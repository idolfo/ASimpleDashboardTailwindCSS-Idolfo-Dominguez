# Software Specification: Influencer Performance Dashboard

**Status:** Approved baseline for the assignment  
**Scope:** Static, responsive front-end demonstration using the prepared sample CSV; no live integrations

## 1. Purpose

Provide a single dashboard view that demonstrates how an influencer could review consolidated performance across social platforms, promoted products, and campaigns. The submission is evaluated primarily on semantic HTML, Tailwind CSS use, clear dashboard structure, and responsive behavior—not on whether a particular set of KPI choices is ideal for the business.

## 2. Users and use cases

The primary user is an influencer or creator who wants to scan performance and identify useful comparisons. The user should be able to:

- Scan headline outcomes quickly.
- Compare performance drivers across platforms and products.
- Review operational details in tables or lists.
- Understand the displayed metrics as a view over prepared data rather than live platform connections.
- Understand when displayed figures are illustrative rather than real.

### FR-0: Prepared local dataset

Dashboard metrics shall be based on the prepared local CSV at `data/sample-data.csv`, rather than unrelated invented literals. Since project-authored JavaScript is prohibited, values are rendered into static HTML and manually reconciled with the CSV. The rendered page shall show the sample status and reporting period. See `data-contract.md` for schema and validation rules.

## 3. Functional/content requirements

### FR-1: Three dashboard blocks

The dashboard shall visibly separate content into these three ordered blocks:

1. Outcome KPIs.
2. Performance drivers.
3. Operational details.

### FR-2: KPI block

The top block shall display **at least three KPIs** in a consistent card pattern. Suitable examples include conversions/sales, commission, reach/impressions, or total interactions. Each KPI shall have a clear label, value, unit/context, and be traceable to the prepared dataset or a documented calculation. Rate metrics are optional and, if shown, require a stated denominator.

### FR-3: Driver block

The middle block shall include **at least three driver views**. Examples include platform comparison, product comparison, a conversion funnel, engagement breakdown, or publishing activity. Each view shall make its purpose and any units/categories understandable. CSS-only charts are optional; simple readable comparisons are acceptable.

### FR-4: Operational details

The bottom block shall contain **at least one useful table or list**. Suitable content includes products, platforms, campaigns, rankings, alerts, or improvement opportunities. Tabular data shall use appropriate table semantics and meaningful headers.

### FR-4a: Optional/static controls

The dashboard is a static presentation. Do not add nonfunctional filters, date pickers, buttons, or navigation controls that imply behavior not implemented. Any connector status must be informational text, clearly indicate “planned” or “not connected,” and not look like an actionable connect button.

### FR-5: Business facts

Where product/commission facts are shown, values shall be accurate:

| Product | Price | 15% commission per sale |
| --- | ---: | ---: |
| Product A | €50.00 | €7.50 |
| Product B | €120.00 | €18.00 |
| Product C | €80.00 | €12.00 |

No actual performance or advertising-cost data was supplied. Prepared figures shall be explicitly labeled as sample/illustrative. Keep summaries and rows internally coherent, and ROI shall not be presented as actual/factual without advertising cost data.

### FR-7: Connector placeholders and future scope

No live platform connectors shall be implemented in this assignment. If connector placeholders are shown in the UI, they shall be clearly marked as planned/not connected and shall not appear functional. High-level remaining connector work shall be documented, including API/permission discovery, authorization and credential security, metric mapping, ingestion/retries/rate limits, validation/privacy, and conversion attribution. See `context.md` and `data-contract.md`.

### FR-8: Aggregation consistency

Any displayed totals or comparisons derived from records shall reconcile with `data/sample-data.csv`. For aggregated rates, compute the ratio from aggregated numerators and denominators (not an unweighted average of row-level rates). If assumptions or source limitations prevent a reliable calculation, omit the metric or label the limitation.

### FR-6: Accessible content and semantics

The document shall use an appropriate page title, semantic structural landmarks, a logical heading hierarchy, descriptive labels, and sufficient text context for displayed metrics. Images are not required for this project; decorative visuals must not replace essential textual labels.

## 4. Non-functional requirements

### NFR-1: Technology

- Use HTML and Tailwind CSS v4 only.
- Do not add project-authored JavaScript; the Tailwind CDN script is the only script allowed by default.
- Load Tailwind with the official browser CDN snippet:

  ```html
  <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
  ```

- Do not use React, Vue, other JavaScript frameworks, other CSS frameworks, `cdn.tailwindcss.com`, or Tailwind v3 setup.
- Use Tailwind utility classes for styling. No custom CSS is expected; narrowly scoped CSS is only allowed if needed for a CSS-only chart.

### NFR-2: Responsive, mobile-first layout

- Start with small-screen styles and enhance using all three responsive breakpoint variants: `sm:`, `md:`, and `lg:`.
- The page shall remain usable at phone, tablet, and desktop viewport sizes (at least three distinct sizes).
- No page-level horizontal scrolling or clipped essential content shall occur at phone width.
- Cards, driver views, and operational details shall reflow appropriately as space changes.

### NFR-3: Consistency and maintainability

Similar cards and widgets shall use consistent visual patterns. Use straightforward, readable static HTML and avoid unnecessary dependencies or abstractions.

## 5. Acceptance and verification

A reviewer can verify the requirements by inspecting the HTML and rendered page:

- [ ] The page clearly displays KPI, driver, and operational blocks in that order.
- [ ] The KPI block contains at least three labeled KPIs.
- [ ] The driver block contains at least three distinct comparison/explanation views.
- [ ] The operational block contains at least one readable table or list.
- [ ] Semantic landmarks, heading order, and table headers are appropriate.
- [ ] Product prices and commission amounts are accurate if shown.
- [ ] Displayed sample-derived totals reconcile to the prepared CSV; rates use clearly stated denominators and correct aggregation.
- [ ] Sample data and missing-cost limitations are made clear; ROI is not falsely asserted.
- [ ] No nonfunctional controls imply filtering, navigation, or active connector behavior.
- [ ] Active HTML uses the Tailwind v4 CDN, not v3 or `cdn.tailwindcss.com`.
- [ ] No prohibited framework or CSS framework is introduced.
- [ ] At phone, tablet, and desktop widths, content reflows and remains legible without page-level horizontal overflow.
- [ ] Styling uses Tailwind utilities and repeated components appear consistent.

## 6. Out of scope

- Connecting to real social-media APIs or analytics providers (documented future work only).
- Authentication, persistence, live filters, or backend data processing.
- A requirement for specific real-world KPI values, chart libraries, photos, or brand assets.
- A production-ready financial ROI calculation without campaign cost inputs.
