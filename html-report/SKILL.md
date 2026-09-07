---
name: html-report
license: MIT
description: Package completed analyses, audits, comparisons, research, or test results as a polished single-file HTML report. Use when the user requests an HTML report or invokes this skill. Do not use for ordinary application pages or to replace an explicitly requested non-HTML format.
metadata:
  author: gmaiolo
  version: "1.0.0"
---

# HTML Report

Apply this workflow only to the HTML output the user requests, including through explicit invocation of this skill. Preserve any explicitly requested Word, PDF, Markdown, or other formats.

Complete the underlying task first, then make one `.html` file the primary deliverable. Preserve the task's rigor and evidence; the report is a presentation layer, not a substitute for the work.

## Deliverable contract

- Produce exactly one HTML file. Inline custom CSS, JavaScript, SVG, and essential images when practical. Do not require a build step, local server, or companion asset.
- Official HTTPS CDN dependencies are allowed when they materially improve charts, diagrams, syntax highlighting, or substantial interaction. Prefer inline CSS for simple report styling; Tailwind's official browser CDN is allowed when its utility styling genuinely reduces complexity, but it is not the default.
- Use the fewest external dependencies possible, pin explicit versions when the provider supports it, and avoid trackers or externally hosted fonts. Keep headline conclusions and exact results readable if JavaScript or a CDN fails whenever practical; otherwise state the online requirement prominently in the report metadata.
- Prefer semantic HTML and native `<details>` disclosure; add scripts only when they materially improve comprehension or navigation.
- Write the file to the user's requested location. Otherwise use a concise descriptive filename in the current workspace. Open or preview it when the environment supports that, and return a direct file link.
- Do not paste the full report into chat. Summarize the outcome briefly and link the artifact.

## Information design

Design for a reader who first wants the answer, then the exceptions, then the proof:

1. Put the title, scope, overall status, and decisive conclusion in the first viewport.
2. Show a compact summary of the most important findings or metrics.
3. Present the main results using the smallest suitable form: prose for a conclusion, a table for exact comparisons, or a restrained chart only when it reveals a relationship faster.
4. Add an **Outliers and exceptions** section only when meaningful anomalies, failures, risks, or edge cases exist. State why each item is unusual and its likely impact.
5. Put methodology, assumptions, limitations, source references, and debug evidence after the results. Collapse dense diagnostics with `<details>` while keeping failures and caveats visible.

For debug evidence, include only what helps reproduce or inspect the result: relevant inputs, checks performed, error summaries, timestamps when material, and links or identifiers for source artifacts. Never expose secrets, tokens, private data, or irrelevant raw logs. Mark missing, partial, stale, or inferred data explicitly.

## Visual standard

- Use a restrained professional system-font design, neutral canvas, one accent color, high contrast, generous spacing, and a readable content width.
- Use consistent status semantics for success, warning, failure, and neutral information. Never rely on color alone.
- Avoid ornamental gradients, oversized hero text, excessive cards, decorative icons, animation, and dashboard clutter.
- Make tables scannable and responsive. Keep exact values available even when using charts.
- Support keyboard navigation, visible focus, reduced motion, narrow screens, and printing. Include a useful `<title>` and descriptive headings.

## Verification

Before delivery, verify that the file opens directly, all intended CDN resources load over HTTPS, fallback content remains useful where required, the layout works at desktop and narrow widths, and there are no obvious browser-console errors. Check that the headline conclusions match the underlying evidence and that every reported outlier is traceable to it.
