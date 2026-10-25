# Prepared Data Contract

## Purpose and status

This contract defines the prepared local dataset used to populate the first dashboard prototype. It is an offline/static input for the UI—not data fetched from social platforms. Since verified business metrics have not been provided, all performance records must be clearly labeled **Sample data** and include a reporting period.

## Proposed representation

Store the canonical prepared dataset at `data/sample-data.csv`. CSV is chosen because the first dataset is a small flat table that is easy to edit and review in spreadsheet software. This is the human-editable source of truth for sample performance records. The dashboard may not use project-authored JavaScript to dynamically load or transform a JSON/CSV file. For this static assignment, values from the CSV are rendered into the HTML manually and kept consistent with the source file. If the team later changes that constraint, the data-loading implementation must be specified and reviewed separately.

For the initial assignment scope, one prepared reporting period and a compact set of internally consistent rows are sufficient. Do not create a larger synthetic dataset than needed to demonstrate the required KPI, driver, and operational blocks.

## Canonical entities and fields

Fields below are a starting contract. Keep only those needed for the actual UI, but preserve their meanings and units.

### Products

| Field | Meaning | Requirement |
| --- | --- | --- |
| `product_id` | Stable product identifier | Required |
| `product_name` | Display name | Required |
| `unit_price_eur` | Product sale price | Required; match project facts |
| `commission_rate` | Commission fraction | Required; `0.15` |

### Performance records

Each row in `data/sample-data.csv` represents one product/platform/campaign combination over the report period, or a documented lower-granularity period if available. The CSV uses one denormalized row per performance record and these headers:

```text
period_start,period_end,data_status,currency,product_id,product_name,unit_price_eur,commission_rate,platform,campaign_id,campaign_name,reach,impressions,likes,comments,shares,saves,interactions,clicks,conversions,ad_cost_eur
```

Required metadata columns on every row keep the CSV self-describing:

| Field | Meaning | Requirement |
| --- | --- | --- |
| `period_start` | Inclusive start date for the report | Required; ISO date (`YYYY-MM-DD`) |
| `period_end` | Inclusive end date for the report | Required; ISO date (`YYYY-MM-DD`) |
| `data_status` | Provenance label | Required; use `sample` until verified data is provided |
| `currency` | Currency used for product/revenue amounts | Required; `EUR` for this project |

`ad_cost_eur` may be blank when no cost data is supplied; a blank means unknown/not provided, not zero. Engagement breakdown columns are required when `interactions` is provided, and `interactions` must equal likes + comments + shares + saves for this sample contract.

| Field | Meaning | Requirement |
| --- | --- | --- |
| `platform` | Source platform (e.g. Instagram, TikTok, YouTube) | Required for platform comparisons |
| `campaign_id` / `campaign_name` | Campaign identity | Optional if campaign detail is displayed |
| `product_id` | Product promoted or sold | Required for product comparison |
| `reach` | Unique accounts reached | Non-negative integer; distinguish from impressions |
| `impressions` | Total content/ad displays | Optional; non-negative integer |
| `interactions` | Engagement actions | Non-negative integer; define included action types |
| `clicks` | Tracked outbound/affiliate clicks | Optional; requires attribution/tracking definition |
| `conversions` | Attributed completed sales | Non-negative integer; attribution method must be stated |
| `ad_cost_eur` | Advertising spend | Optional; if missing, ROI is unavailable |

If displaying detailed engagement, use a consistent breakdown (e.g. likes, comments, shares, saves) whose sum equals `interactions`, or explain why the values differ. Do not fabricate precision that the source data cannot support.

## Derived metrics and validation

- **Commission per unit:** `unit_price_eur × commission_rate`. At 15%: Product A = €7.50, Product B = €18.00, Product C = €12.00.
- **Commission earned:** `conversions × unit commission`, assuming each conversion is one completed eligible sale and there are no refunds/adjustments. The current sample uses this assumption.
- **Engagement rate:** if used, define it as `interactions ÷ reach × 100`; omit or mark unavailable when reach is zero/missing.
- **Conversion rate:** choose and label the denominator. For example, `conversions ÷ reach × 100` differs from `conversions ÷ clicks × 100`; do not mix these definitions.
- **ROI:** do not show as a factual result without a suitable cost basis. If later defined, document the exact numerator, denominator, attribution window, and treatment of commission/revenue before calculating it.
- Validate non-negative counts, known product IDs, valid dates, matching currencies, and coherent aggregation between records and displayed summaries. For totals, sum record numerators/denominators first; do not sum reach as unique cross-platform people or average row rates without weighting.
- Keep rounding consistent; preserve exact commission arithmetic before display rounding.

## Initial sample coverage

Include a compact set of records that supports the required dashboard comparisons: all three products and at least three example platforms (Instagram, TikTok, YouTube). Use a single clearly stated period unless the dashboard explicitly compares periods. Keep campaign names fictional. Sample counts may be illustrative, but derived totals displayed in the HTML must reconcile to the CSV. Summed platform reach represents platform-level reach totals, not deduplicated people across platforms; label it accordingly if shown.

The current prepared sample covers **2026-09-01 through 2026-09-30**, includes all three products on Instagram, TikTok, and YouTube, and leaves `ad_cost_eur` blank because cost data was not supplied. Its values are illustrative only.

## Privacy and provenance

Use synthetic example data for the prototype. Do not add real account names, personal identifiers, access tokens, customer data, or credentials. If verified data is introduced later, record its source, permitted use, report period, timezone, extraction date, and any caveats without committing secrets or sensitive personal information.

## Future platform connector placeholder

Connectors are not part of the current implementation and must not be implied to be active. Future work, before implementation:

1. Choose initial platforms and review API availability, permissions, account eligibility, review requirements, rate limits, and terms.
2. Define secure OAuth/account authorization and token storage, renewal, revocation, and access boundaries.
3. Map platform-specific metrics to this contract and document definition gaps and incomparable measures.
4. Plan ingestion schedules, pagination, retries, rate-limit behavior, backfills, and freshness/error indicators.
5. Establish validation, deduplication, privacy/security safeguards, retention rules, and automated tests with approved fixtures.
6. Define campaign-link and sales attribution (for example affiliate tracking); platform analytics alone may not prove that a platform caused a sale.
7. Decide how imported records are reviewed and reconciled with product sales and commission records.

The dashboard may include a static note such as “Platform connections: planned” or “No accounts connected.” Such copy is informational only and must not look like a working connect control.
