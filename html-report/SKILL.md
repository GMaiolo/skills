---
name: html-report
license: MIT
description: Package completed analyses, audits, comparisons, research, or test results as a polished single-file HTML report. Use when the user requests an HTML report or invokes this skill. Do not use for ordinary application pages or to replace an explicitly requested non-HTML format.
metadata:
  author: gmaiolo
  version: "1.1.0"
---

# HTML Report

Apply this workflow only to the HTML output the user requests, including through explicit invocation of this skill. Preserve any explicitly requested Word, PDF, Markdown, or other formats.

Complete the underlying task first, then make one `.html` file the primary deliverable. Preserve the task's rigor and evidence; the report is a presentation layer, not a substitute for the work.

## Deliverable contract

- Produce exactly one HTML file with inline React JSX, compiled in the browser by Babel Standalone. Inline custom CSS, report data, SVG, and images when practical. Do not require package installation, a build step, local server, or companion files other than images or videos. Reference companion images or videos with relative paths and deliver them with the HTML.
- Load React, React DOM, Babel Standalone, and additional browser libraries from reputable HTTPS CDNs. Prefer Tailwind's browser CDN when utilities simplify styling, but inline CSS is also fine.
- Use the fewest external dependencies possible, pin explicit versions when the provider supports it, and avoid trackers or externally hosted fonts. Keep headline conclusions and exact results readable if JavaScript or a CDN fails whenever practical; otherwise state the online requirement prominently in the report metadata.
- Prefer semantic HTML within React components and native `<details>` disclosure; add interactions only when they materially improve comprehension or navigation.
- Write the file to the user's requested location. Otherwise use a concise descriptive filename in the current workspace. Open or preview it when the environment supports that, and return a direct file link.
- Do not paste the full report into chat. Summarize the outcome briefly and link the artifact.

## Inline React workflow

Adapt [assets/example.html](assets/example.html), a minimal demo. Replace sample content and remove unused features and dependencies.

CDN dependencies require internet access. Tailwind's [Play CDN](https://tailwindcss.com/docs/installation/play-cdn) is intended for development.

- Load [Babel Standalone](https://babeljs.io/docs/babel-standalone) before `<script type="text/babel" data-type="module">`. Set the React preset's `runtime` to `automatic`.
- Place the import map before module execution. Map `react`, `react-dom`, `react/jsx-runtime`, and `react-dom/client` to matching, pinned ESM versions. Render with `createRoot` from `react-dom/client`.
- Babel transforms JSX but does not resolve packages. Map bare imports and load each library's required CSS. Share one React instance; with [esm.sh](https://esm.sh/#using-import-maps), use `?external=react,react-dom` and map any other external peers.
- For delivered reports, keep a static summary outside the React root when practical. Render data as text, avoid raw HTML interpolation, and escape `<` as `\u003c` in serialized inline data.

## Information design

Design for a reader who first wants the answer, then the exceptions, then the proof:

1. Put the title, scope, overall status, and decisive conclusion in the first viewport.
2. Show a compact summary of the most important findings or metrics.
3. Present the main results using the smallest suitable form: prose for a conclusion, a table for exact comparisons, or a restrained chart only when it reveals a relationship faster.
4. Add an **Outliers and exceptions** section only when meaningful anomalies, failures, risks, or edge cases exist. State why each item is unusual and its likely impact.
5. Put methodology, assumptions, limitations, source references, and debug evidence after the results. Collapse dense diagnostics with `<details>` while keeping failures and caveats visible.

For debug evidence, include only what helps reproduce or inspect the result: relevant inputs, checks performed, error summaries, timestamps when material, and links or identifiers for source artifacts. Never expose secrets, tokens, private data, or irrelevant raw logs. Mark missing, partial, stale, or inferred data explicitly.

## Explaining flows

You can use [React Flow](https://reactflow.dev) (`@xyflow/react`) to explain workflows, decisions, or data flow:

- Pin the latest compatible stable release and load its `dist/style.css` after Tailwind, if present. See the [setup guide](https://reactflow.dev/learn) and [API reference](https://reactflow.dev/api-reference).
- Set the container's width and height, arrange nodes in reading order, label branches, and use `fitView`. Default to read-only, allowing pan and zoom when useful.
- Use `animated: true` or SVG `<animateMotion>` when motion clarifies direction; see [Animating Edges](https://reactflow.dev/examples/edges/animating-edges). Delivered reports should show static connections for reduced motion and printing; the minimal example only demonstrates animation.

## Visual standard

- Use a restrained professional system-font design, neutral canvas, one accent color, high contrast, generous spacing, and a readable content width.
- Use consistent status semantics for success, warning, failure, and neutral information. Never rely on color alone.
- Avoid ornamental gradients, oversized hero text, excessive cards, decorative icons, decorative animation, and dashboard clutter.
- Make tables scannable and responsive. Keep exact values available even when using charts.
- Support keyboard navigation, visible focus, reduced motion, narrow screens, and printing. Include a useful `<title>` and descriptive headings.

## Verification

Open the report via `file://` and test its interactions. Check CDN loading, JSX compilation, imports without duplicate React instances, Tailwind styling when used, and console errors. Confirm it needs no server or companion files other than images or videos, and that relative image/video paths resolve. Check desktop and narrow layouts, and any static fallback with JavaScript disabled or CDN requests blocked. Babel and Tailwind development warnings are expected. Verify that conclusions and outliers match the evidence.
