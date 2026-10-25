# Project Context

## Purpose

This is a beginner-friendly, static web UI project: **A Simple Dashboard with Tailwind CSS**. It presents an influencer's cross-platform marketing performance in one scannable view to support quick business decisions.

## Business scenario

An influencer is beginning to work with brands and promote products on social platforms such as Instagram, TikTok, and YouTube. Their performance information is scattered across accounts. The dashboard concept consolidates that information so the influencer can compare outcomes by product, platform, and campaign.

## Business questions

- How much commission has been earned?
- Which products generate the most sales and commissions?
- How well do ads convert relative to reach?
- Which platforms provide the best return relative to costs?
- What is the engagement rate by platform and product?

## Source business facts

The influencer earns a **15% commission on each product sale**.

| Product | Sale price | Commission per sale |
| --- | ---: | ---: |
| Product A | €50.00 | €7.50 |
| Product B | €120.00 | €18.00 |
| Product C | €80.00 | €12.00 |

## Data approach and limitations

The first dashboard version will use a **prepared, local dataset** as its source of metrics. The dataset is static input for a visual prototype; it is not live data and does not imply that platform accounts are connected. Use a clear data period and label the dataset/demo figures as sample data unless verified business data is later supplied.

The project currently has no actual sales, reach, impressions, engagement, campaign, or advertising-cost data. Sample rows should be internally coherent, and derived commission values should follow the 15% rule above. ROI requires advertising-cost inputs and must not be represented as factual without them.

## Future platform connector work (not current scope)

Platform connectors remain placeholders only. High-level work required before implementing them includes:

1. Select the initial platforms and identify their available APIs, permissions, account types, rate limits, review requirements, and terms of use.
2. Define secure account authorization and credential/token storage, including renewal and revocation.
3. Map each platform's source metrics into the prepared dataset's canonical schema; document incompatible or missing metrics and differences in metric definitions.
4. Design ingestion scheduling, pagination, retries, rate-limit handling, backfills, and data freshness/error reporting.
5. Add validation, deduplication, privacy/security controls, and tests using approved API fixtures or sandbox data.
6. Confirm how clicks and sales are attributed to a platform/campaign (for example, affiliate tracking); platform reach alone cannot reliably attribute a sale.

Connector implementation, live data collection, authentication, and backend behavior are future work, not part of this static assignment. See `data-contract.md` for the initial prepared-data contract.

## Scope boundary

This assignment is a static front-end demonstration backed by prepared local sample data, not a connected analytics product. See `spec.md` for implementation constraints and acceptance criteria.
