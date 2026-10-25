# AI Contributor Instructions

These instructions apply to the entire repository. Follow them whenever you inspect, plan, or change project files.

## Read first

Before implementation, read `context.md`, `briefing.md`, `spec.md`, `plan.md`, and `tasks.md`. Treat `spec.md` as the source of truth for acceptance requirements. If documents conflict, do not silently choose: reconcile the documents and keep business facts in `context.md`, product requirements in `spec.md`, and implementation choices in `plan.md`.

## Non-negotiable technology constraints

- This is an **HTML and Tailwind CSS v4 only** project.
- Do not add project-authored JavaScript, React, Vue, JavaScript frameworks, build systems, component libraries, or other CSS frameworks. The Tailwind CDN script is the sole script allowed by default.
- Use the official Tailwind CSS v4 browser CDN snippet in the HTML `<head>`:

  ```html
  <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
  ```

- Never use `https://cdn.tailwindcss.com`, Tailwind v3 CDN snippets, or Tailwind v3 setup instructions.
- Style with Tailwind utility classes. Do not add custom stylesheets or inline style attributes; narrowly scoped CSS is permitted only when the specification requires a CSS-only chart and utility classes are insufficient.
- Do not introduce image assets or an `assets/images` directory unless the user provides a real asset requirement. Photos are not needed for the agreed scope.

## Implementation practices

- Use semantic HTML landmarks and a logical heading hierarchy. Use native links, buttons, and table markup appropriately.
- Design mobile-first. Use and check Tailwind `sm:`, `md:`, and `lg:` responsive variants for phone, tablet, and desktop layouts (at least three breakpoint variants).
- Prevent horizontal overflow at small viewports. For genuinely wide tabular data, adapt the presentation or contain overflow within the table region rather than allowing the whole page to scroll horizontally.
- Keep repeated KPI cards, widgets, and table patterns consistent. Favor straightforward, readable markup over abstractions that require JavaScript.
- Keep sample figures clearly identified as sample data. Do not claim factual ROI without supplied cost data.
- Use the prepared local dataset contract in `data-contract.md` as the source for dashboard metric values. Keep its sample status and period visible, and maintain internal consistency. Do not add live platform connectors; placeholders must be visibly nonfunctional and identified as not connected.
- Do not add code to load or transform a JSON dataset in the browser: that would require project-authored JavaScript, which is prohibited. Prefer static rendered HTML sourced from the prepared dataset unless the user changes the technology constraint.
- Avoid unnecessary dependencies, generated files, and unrelated edits. Preserve the repository's existing Flask development server unless the user asks otherwise.
- Keep documentation aligned: context is business background, spec is testable behavior, plan records intended structure, and tasks track implementation progress.

## SDD workflow

Use the sequence **Specify → Plan → Tasks → Implement → Verify**. Do not jump to implementation when requirements are ambiguous. Keep each task small and checkable; update `tasks.md` as work progresses. If a change reveals a specification gap, update the spec before or alongside implementation.

## Verification before reporting completion

- Confirm the page uses semantic structure and contains the three required dashboard blocks.
- Check KPI/driver/operational requirements and business values against `spec.md` and `context.md`.
- Check the displayed dataset's structure, sample disclosure, period, and consistency against `data-contract.md`; verify connector placeholders are not presented as active integrations.
- Inspect the page at narrow phone, tablet, and desktop widths; confirm there is no page-level horizontal overflow or broken section layout.
- Search the project for prohibited frameworks, CSS frameworks, `cdn.tailwindcss.com`, and Tailwind v3 references (distinguish prohibitions/documentation from active code where appropriate).
- Check links and local run instructions. Report what was and was not verified; do not claim browser testing if it was not performed.
