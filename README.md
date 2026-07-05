<div align="center">

# CSS Pro-Tips

**A validated, Baseline-aware modern CSS skill for AI coding agents.**

Drop it into Claude Code, Codex, Cursor, Pi, OpenCode, Kiro — or any agent that reads
[`SKILL.md`](./SKILL.md) — and your agent writes idiomatic, browser-safe CSS instead of
copy-pasted hacks from 2015.

[![npm version](https://img.shields.io/npm/v/css-pro-tips.svg)](https://www.npmjs.com/package/css-pro-tips)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
[![Baseline-aware](https://img.shields.io/badge/Baseline-aware-success.svg)](https://web.dev/baseline)
[![Agent Skill](https://img.shields.io/badge/format-SKILL.md-7c3aed.svg)](https://developers.openai.com/codex/skills)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](#contributing)
[![Maintained by Pythoughts](https://img.shields.io/badge/maintained%20by-Pythoughts-0b7285.svg)](https://github.com/Pythoughts-labs)

</div>

---

## Why this exists

Most CSS advice an agent has absorbed is a mix of timeless patterns and outdated hacks —
`float` clearfixes, `padding-bottom` ratio boxes, `100vh` mobile bugs, `:focus` rings on
every mouse click. This skill gives the agent **one curated file** that:

- Keeps the **evergreen** tips that still hold up (resets, `:not()`, `aspect-ratio`, logical properties).
- Adds a **Modern CSS** section bucketed by [MDN Baseline](https://web.dev/baseline) —
  `:has()`, container queries, `@layer`, `subgrid`, `color-mix()`, `light-dark()`,
  `@scope`, anchor positioning, scroll-driven animations, and more.
- **Labels every modern feature** as 🟢 Widely / 🟡 Newly / 🔴 Limited, with a graceful
  `@supports` fallback for anything not yet safe to ship unconditionally.

Every status claim was verified against MDN's per-feature Baseline data and the
[`web-platform-dx/web-features`](https://github.com/web-platform-dx/web-features) dataset
(last validated **July 2026**). Baseline is a *browser-compatibility* signal only — the
skill still tells the agent to test accessibility, motion preferences, keyboard behavior,
and contrast separately.

## What's inside

A single self-contained skill: [`SKILL.md`](./SKILL.md) (skill name: `css-protips`).

| Section | Covers |
|---------|--------|
| **Evergreen tips** | Resets, `box-sizing` inheritance, `:not()` navigation, `aspect-ratio`, `:is()`, intrinsic sizing, focus styling, mobile form fixes |
| **Baseline 🟢 Widely** | `:has()`, `@container`, native nesting, `@layer`, `subgrid`, `color-mix()`, logical properties, `:focus-visible`, `clamp()` |
| **Baseline 🟡 Newly** | `text-wrap`, `light-dark()`, `@scope`, `@starting-style`, `contrast-color()`, anchor positioning, `field-sizing` |
| **🔴 Limited** | `accent-color`, scroll-driven animations, `interpolate-size`, `calc-size()`, `transition-behavior` — all with `@supports` gates |
| **Modern additions** | `@property`, container query units, popovers, top-layer transitions, `scrollbar-gutter`, `content-visibility`, View Transitions, custom highlights, scroll-state queries |
| **Modernize older tips** | When to retire the padding-hack ratio box, `max-height` sliders, `* + *` owl, `local()` fonts |

---

## Install

The fastest path is npm — it fetches the skill into `node_modules/css-pro-tips/`, then you
copy `SKILL.md` into your agent's skills directory.

```bash
npm install css-pro-tips
```

Then pick your agent below. (No npm? Just download [`SKILL.md`](./SKILL.md) directly and
copy it into the same path.)

### Claude Code

```bash
mkdir -p ~/.claude/skills/css-protips
cp node_modules/css-pro-tips/SKILL.md ~/.claude/skills/css-protips/
```

Project-scoped instead? Use `.claude/skills/css-protips/SKILL.md` in your repo.
Restart Claude Code; it auto-discovers the skill by its frontmatter.

### OpenAI Codex CLI

```bash
mkdir -p ~/.codex/skills/css-protips
cp node_modules/css-pro-tips/SKILL.md ~/.codex/skills/css-protips/
```

For a team repo, check it into `.agents/skills/css-protips/SKILL.md` instead.
Codex recognizes any directory containing a file named exactly `SKILL.md`.
([docs](https://developers.openai.com/codex/skills))

### OpenCode

```bash
mkdir -p .opencode/skills/css-protips
cp node_modules/css-pro-tips/SKILL.md .opencode/skills/css-protips/
```

OpenCode also reads `.claude/skills/` and `.agents/skills/`, so if you've already installed
for Claude Code or Codex in the same repo, OpenCode picks it up with no extra step.
([docs](https://opencode.ai/docs/skills/))

### Pi (`@earendil-works/pi-coding-agent`)

```bash
mkdir -p ~/.pi/skills/css-protips
cp node_modules/css-pro-tips/SKILL.md ~/.pi/skills/css-protips/
```

Invoke it in a session with `/skill:css-protips`.
([docs](https://github.com/earendil-works/pi/blob/main/packages/coding-agent/docs/skills.md))

### Cursor

Cursor uses **rules** (`.mdc`), not `SKILL.md`. Reference the skill from a rule so Cursor
loads it on CSS work:

```bash
mkdir -p .cursor/rules
cp node_modules/css-pro-tips/SKILL.md .cursor/rules/css-protips.mdc
```

Then add this frontmatter to the top of `.cursor/rules/css-protips.mdc`:

```mdc
---
description: Modern, Baseline-aware CSS patterns and pro-tips
globs: ["**/*.css", "**/*.scss", "**/*.{tsx,jsx,vue,svelte,astro}"]
alwaysApply: false
---
```

### Kiro

Kiro uses **steering files** (plain markdown):

```bash
mkdir -p .kiro/steering
cp node_modules/css-pro-tips/SKILL.md .kiro/steering/css-protips.md
```

Use `~/.kiro/steering/` for a global, all-workspace install.
([docs](https://kiro.dev/docs/steering/))

### Any other agent

The skill is plain Markdown with YAML frontmatter. Point your agent's instruction file
(`AGENTS.md`, a system prompt, a rules file) at `SKILL.md`, or paste its contents in. The
`.agents/skills/` and `.claude/skills/` conventions are honored by a growing set of agents.

---

## Updating

```bash
npm update css-pro-tips
# then re-copy SKILL.md into your agent's skills dir
```

On a Mac/Linux box, symlink instead of copy to stay current automatically:

```bash
ln -sf "$(pwd)/node_modules/css-pro-tips/SKILL.md" ~/.claude/skills/css-protips/SKILL.md
```

---

## Credits

- Baseline statuses sourced from [MDN](https://developer.mozilla.org/),
  [web.dev/baseline](https://web.dev/baseline), and
  [`web-platform-dx/web-features`](https://github.com/web-platform-dx/web-features).


## Contributing

PRs welcome. When adding or changing a modern-CSS claim, **cite the Baseline status** (with a
source) so the file stays verifiable. Keep the evergreen tips evergreen — if a tip is
superseded by a native feature, add it to the "Modernize older tips" section rather than
deleting the original.

## Author & maintainer

Created by **Mohamed Elkholy** — [@mohamed-elkholy95](https://github.com/mohamed-elkholy95).
Maintained under [**Pythoughts**](https://github.com/Pythoughts-labs).

## License

[MIT](./LICENSE) © 2026 Mohamed Elkholy
