# Skills

Reusable [Agent Skills](https://agentskills.io/) for coding agents, installable with the [skills CLI](https://skills.sh/docs/cli).

## Available skills

| Skill | Purpose |
| --- | --- |
| [html-report](html-report/SKILL.md) | Present completed analyses, audits, comparisons, research, or test results as a single HTML report. |
| [succinct](succinct/SKILL.md) | Keep writing, explanations, plans, and code clear, simple, and concise. |

## Installation

Install from this repository:

```sh
npx skills add gmaiolo/skills
```

To install a specific skill, use its name:

```sh
npx skills add gmaiolo/skills --skill html-report
npx skills add gmaiolo/skills --skill succinct
```

To list available skills without installing:

```sh
npx skills add gmaiolo/skills --list
```

## Example prompts

**HTML report**

> Use $html-report to turn these audit findings into a single HTML report with a summary, supporting evidence, and limitations.

**Succinct**

> Use $succinct to tighten this proposal while preserving the key decisions and rationale.

> Use $succinct to keep this code change simple and explain the result concisely.

## License

Licensed under the [MIT License](LICENSE).
