# Implementation Tasks

This checklist tracks implementation of the assignment scope in `spec.md`. Mark a task complete only after its stated verification is performed. Dataset preparation and static page implementation are complete; rendered browser checks remain unavailable in this environment.

## Status key

- `[ ]` Not started
- `[~]` In progress
- `[x]` Completed and verified

## T1 — Confirm starter and scope

- [x] Inspect the existing Flask server route for root `index.html` and static-file serving (runtime not verified; Flask is not installed here).
- [x] Review `context.md`, `briefing.md`, `spec.md`, `plan.md`, and `data-contract.md` before page implementation.
- **Verify:** confirm deliverable remains one static HTML/Tailwind v4 page with prepared data; connectors/interactivity remain out of scope.

## T2 — Prepare and validate sample data

- [x] Create `data/sample-data.csv` following `data-contract.md`.
- [x] Include all three products and Instagram, TikTok, and YouTube for a clearly stated period.
- [x] Mark values as sample and leave unknown ad cost blank.
- [x] Validate required headers, dates, product facts, nonnegative counts, interaction subtotals, and commission arithmetic.
- **Remaining verification:** when implementing the page, reconcile all rendered totals and rates with the CSV.

## T3 — Build semantic page skeleton

- [x] Create root `index.html` with metadata and the exact Tailwind CSS v4 browser CDN.
- [x] Add semantic header, main heading, and the three ordered dashboard sections.
- [x] Avoid dummy navigation or controls that imply unsupported behavior.
- **Verify:** source-inspected document outline, landmarks, navigation targets, and script tags; HTML parser check passed.

## T4 — Present KPI outcomes

- [x] Add at least three consistent KPI cards using prepared data and/or documented calculations.
- [x] Include clear labels, units/context, sample status, and report period.
- **Verify:** independent reviews and a local script recomputed displayed totals from the CSV; engagement denominator is stated.

## T5 — Present performance drivers

- [x] Add at least three distinct, labeled driver views (platform comparison, product commission, engagement breakdown).
- [x] Keep presentation understandable without color alone; CSS-only charts are optional.
- **Verify:** independent metric audits confirmed categories, labels, proportions, and aggregated calculations against CSV.

## T6 — Present operational details

- [x] Add at least one meaningful semantic table or list, using sample records/product facts.
- [x] Explain unknown advertising cost and avoid claiming factual ROI.
- [x] Show connector status only as static “planned/not connected” information.
- **Verify:** source and independent review confirmed table semantics, product/commission figures, provenance, and no fake functional controls.

## T7 — Apply responsive design

- [x] Build mobile-first using Tailwind utilities and `sm:`, `md:`, and `lg:` variants.
- [x] Adapt cards, driver widgets, and operational details to small, medium, and large screens.
- [x] Contain wide table content in a keyboard-focusable local scroll region in source.
- **Verify:** source reviewed by independent auditors; rendered phone/tablet/desktop inspection remains pending because no browser is available. Keep T7 in progress until rendered inspection is performed.

## T8 — Final verification

- [~] Confirm `spec.md` acceptance criteria against source; rendered-page criteria remain unverified.
- [x] Search active implementation for prohibited frameworks, CSS frameworks, Tailwind v3 setup, `cdn.tailwindcss.com`, and project-authored JavaScript; source checks passed.
- [~] Confirm local run instructions and links by source inspection; Flask runtime and browser behavior were not testable because Flask and browsers are unavailable.
- [x] Record unverified browser checks and remaining limitations.
- **Verify:** local HTML parsing and CSV reconciliation passed. Do not mark final verification complete until rendered browser checks are available.

## Deferred connector work

No connector implementation task is part of this assignment. High-level discovery and implementation needs are documented in `context.md` and `data-contract.md`.
