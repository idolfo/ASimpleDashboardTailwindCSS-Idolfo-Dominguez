# Influencer Performance Dashboard

A static, mobile-first dashboard concept for reviewing an influencer's marketing performance across products and social platforms. The project is implemented with semantic HTML and **Tailwind CSS v4**.

## Run locally

This starter repository includes a small Flask development server. Install Flask if needed, then run:

```bash
python3 -m pip install flask
python3 server.py
```

Open `http://localhost:3000` in a browser. The server expects an `index.html` at the repository root. The page loads Tailwind CSS v4 from its browser CDN, so an internet connection is needed for Tailwind styling.

## Project documents

- `context.md` — business background and known facts/data limitations.
- `briefing.md` — assignment overview and evaluation emphasis.
- `spec.md` — normative requirements and acceptance/verification checks.
- `data-contract.md` — prepared local dataset shape and future connector boundary.
- `data/sample-data.csv` — canonical sample performance records used to prepare the static dashboard content.
- `plan.md` — implementation approach and architecture.
- `tasks.md` — small, verifiable work units for the Specify–Plan–Tasks–Implement–Verify workflow.
- `AGENTS.md` — persistent instructions for AI coding assistants.

## Scope and data

The initial dashboard uses a prepared local dataset; it does not connect to social-media platforms. The influencer earns 15% commission per sale: Product A (€50) = €7.50, Product B (€120) = €18.00, and Product C (€80) = €12.00. Since actual campaign, sales, reach, engagement, and advertising-cost data has not been provided, prepared figures are sample data. ROI must not be presented as factual without cost data. Future connector work is documented in `context.md` and `data-contract.md`.
