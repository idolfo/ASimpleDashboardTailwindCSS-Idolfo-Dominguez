# Project Briefing: Influencer Performance Dashboard

## Goal

Create a polished, responsive, static dashboard that demonstrates how an influencer could consolidate performance information across social platforms, products, and campaigns. Prioritize the assignment's evaluated qualities—semantic HTML, Tailwind utility usage, clear section hierarchy, consistent component patterns, and responsive behavior—over the correctness of any particular sample KPI.

## Required three-block structure

1. **Outcome KPIs (top):** show at least three summary KPI cards, such as sales/conversions, commission, reach, engagement, or conversion rate.
2. **Performance drivers (middle):** show at least three meaningful comparisons or explanatory views, such as platform performance, product performance, conversion funnel, engagement breakdown, or publishing activity. CSS-only visualizations are optional.
3. **Operational detail (bottom):** include useful tables or lists, such as product/platform/campaign details, rankings, or opportunities.

Use a prepared local dataset for the dashboard's metrics. Products are priced at €50, €120, and €80; commission is 15% per sale. Actual performance and cost data is not provided, so the initial dataset is sample/illustrative. Identify its period and sample status, keep related values coherent, and do not imply factual ROI. Platform connectors are future placeholders only; document the high-level work remaining rather than implementing integrations.

The page is a static presentation: do not add project-authored JavaScript to load the CSV and do not add nonfunctional filters, buttons, or “connect account” controls. Rendered totals and comparisons should reconcile to the CSV; see `data-contract.md` for aggregation caveats.

## Responsive and implementation expectations

- Start with the smallest viewport and progressively enhance with Tailwind `sm:`, `md:`, and `lg:` breakpoint variants. Ensure usable phone, tablet, and desktop layouts without horizontal page overflow.
- Use semantic document landmarks and appropriate elements (`header`, `nav` when present, `main`, `section`, lists, and correctly structured tables).
- Build with **HTML and Tailwind CSS v4 only**. Use the official browser CDN snippet in the document head. Do not add project-authored JavaScript, React, Vue, JavaScript frameworks, other CSS frameworks, `cdn.tailwindcss.com`, or Tailwind v3 setup.
- Style with Tailwind utility classes. Avoid custom CSS except when specifically needed for a CSS-only chart; do not add photos or an image directory unless the project later has a real need.
- Keep repeated cards and widgets visually consistent. Charts are optional; readable labeled comparisons are sufficient.

## Evaluation focus

- Semantic HTML and logical heading/landmark hierarchy.
- Tailwind utility use without conflicting frameworks or redundant custom styles.
- Clear separation of KPI, driver, and operational blocks.
- Consistent component patterns and visual hierarchy.
- Mobile-first responsive layout at phone, tablet, and desktop widths.

The testable requirements and acceptance checks are in `spec.md`; the prepared-data shape and connector boundary are in `data-contract.md`; implementation guidance is in `plan.md`; work units are tracked in `tasks.md`.
