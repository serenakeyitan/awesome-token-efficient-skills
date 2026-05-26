# awesome-token-efficient-skills

Claude Code skills, ranked by what they cost. Every entry measured in tokens, not estimated.

Most awesome-lists rank by stars or topic. This one ranks by the only thing that actually hurts: how many tokens the skill burns from your context budget before it does anything useful.

> Curated by the [first-tree](https://github.com/unispark-inc/first-tree?ref=awesome-token-efficient-skills) team.

---

## Why this list exists

Steipete put it best ([tweet, 3.2k likes](https://twitter.com/steipete/status/2058917897590673525)):

> *"Folks: when you write skills, ask your agent to be token efficient, relax grammer. I see too many skills that write books in the skill description, and all that crap is loaded into every context."*

Codex burns ~2% of your context window on skill descriptions before you ever ask a question. With a 272k context window that's a ~5,440 token budget. A single bloated `SKILL.md` can eat half of that.

This list shows what good looks like.

---

## How tokens are measured

Roughly `ceil(utf8_bytes / 4)` — the same approximation Codex's `core-skills/src/render.rs` uses for budget enforcement. For exact per-skill measurement, run [steipete/agent-scripts/skills/skill-cleaner](https://github.com/steipete/agent-scripts/tree/main/skills/skill-cleaner). It reads your installed skills and prints budget usage, duplicates, and compaction candidates.

All measurements below are SKILL.md file size at the time of curation. Linked file sizes can drift — re-measure before relying on the number.

---

## The list

| Rank | ~Tokens | Skill | What it does |
|---:|---:|---|---|
| 1 | **151** | [caveman-stats](#1-caveman-stats--151-tokens) | Status snapshot for the caveman skill suite |
| 2 | **265** | [codex-debugging](#2-codex-debugging--265-tokens) | Stuck-debugger reset prompt for Codex |
| 3 | **319** | [gh-address-comments](#3-gh-address-comments--319-tokens) | Reply to and resolve PR review comments |
| 4 | **377** | [internal-comms](#4-internal-comms--377-tokens) | Draft Slack and email updates for an org |
| 5 | **434** | [markdown-converter](#5-markdown-converter--434-tokens) | Convert anything to Markdown |
| 6 | **511** | [caveman-help](#6-caveman-help--511-tokens) | Quick reference for caveman commands |
| 7 | **526** | [peekaboo](#7-peekaboo--526-tokens) | Screenshot helper for agents on macOS |
| 8 | **558** | [brand-guidelines](#8-brand-guidelines--558-tokens) | Anthropic-style brand voice and palette |
| 9 | **620** | [caveman-commit](#9-caveman-commit--620-tokens) | Terse, prefix-locked commit messages |
| 10 | **684** | [caveman-review](#10-caveman-review--684-tokens) | Short-form code review |
| 11 | **724** | [npm](#11-npm--724-tokens) | Dependency-safe npm operations |
| 12 | **771** | [web-artifacts-builder](#12-web-artifacts-builder--771-tokens) | Build single-file HTML/JS artifacts |
| 13 | **781** | [theme-factory](#13-theme-factory--781-tokens) | Generate themed slide/doc/page artifacts |
| 14 | **890** | [skill-cleaner](#14-skill-cleaner--890-tokens) | Audit your installed skills' budget |
| 15 | **978** | [webapp-testing](#15-webapp-testing--978-tokens) | Test live web apps end-to-end |

For comparison, the same family's heaviest skills: `anthropics/skills/skill-creator` at **8,292 tokens**, `claude-api` at **8,260**, `openai/skills/hatch-pet` at **9,324**. A bloated skill description costs as much as 50+ of the entries above.

---

## 1. `caveman-stats` — 151 tokens

Reports caveman's status — installed version, active model, recent token spend. The leanest skill on this list. Proves a useful skill can fit in ~150 tokens.

🔗 https://github.com/JuliusBrussee/caveman/tree/main/skills/caveman-stats

---

## 2. `codex-debugging` — 265 tokens

When Codex gets stuck in a debug loop, this skill resets it with a single-page protocol: reproduce, isolate, fix, verify. No long preamble.

🔗 https://github.com/steipete/agent-scripts/tree/main/skills/codex-debugging

---

## 3. `gh-address-comments` — 319 tokens

Walks through unresolved PR review comments and either applies the change or replies with reasoning. Pairs well with `gh-fix-ci`.

🔗 https://github.com/openai/skills/tree/main/skills/.curated/gh-address-comments

---

## 4. `internal-comms` — 377 tokens

Drafts Slack and email updates that follow Anthropic-internal voice rules. The leanest official Anthropic skill. Lowercase, direct, no marketing speak.

🔗 https://github.com/anthropics/skills/tree/main/skills/internal-comms

---

## 5. `markdown-converter` — 434 tokens

Convert PDFs, HTML, docx, and other formats into clean Markdown. The instructions trust the model to pick the right converter rather than spell every case out.

🔗 https://github.com/steipete/agent-scripts/tree/main/skills/markdown-converter

---

## 6. `caveman-help` — 511 tokens

Lists every caveman command with one-line descriptions. A help screen that does not bloat the routing layer.

🔗 https://github.com/JuliusBrussee/caveman/tree/main/skills/caveman-help

---

## 7. `peekaboo` — 526 tokens

Screenshot helper for agents working on macOS. Captures a window, region, or full screen and saves it where the agent expects.

🔗 https://github.com/steipete/agent-scripts/tree/main/skills/peekaboo

---

## 8. `brand-guidelines` — 558 tokens

Anthropic's official brand voice and visual rules in 558 tokens. Read this when generating customer-facing artifacts. Proof that "brand guidelines" do not require 8k tokens.

🔗 https://github.com/anthropics/skills/tree/main/skills/brand-guidelines

---

## 9. `caveman-commit` — 620 tokens

Forces commit messages into a prefix-locked, lowercase, ≤60-char first-line format. Examples included. No corporate fluff.

🔗 https://github.com/JuliusBrussee/caveman/tree/main/skills/caveman-commit

---

## 10. `caveman-review` — 684 tokens

Code review with a budget. Pulls the diff, scans for the five issues that matter most, and stops. No spurious "consider extracting to a helper" suggestions.

🔗 https://github.com/JuliusBrussee/caveman/tree/main/skills/caveman-review

---

## 11. `npm` — 724 tokens

Safe `npm` operations for agents — checks lockfile drift, refuses to bump majors without a flag, runs audits. The rules fit in under 800 tokens.

🔗 https://github.com/steipete/agent-scripts/tree/main/skills/npm

---

## 12. `web-artifacts-builder` — 771 tokens

Build single-file HTML/JS artifacts the way Claude.ai's artifact mode does. Used internally at Anthropic. Lean by design — the heavy lifting lives in references.

🔗 https://github.com/anthropics/skills/tree/main/skills/web-artifacts-builder

---

## 13. `theme-factory` — 781 tokens

Generate themed slide decks, docs, and landing pages. Composes with the `pptx`, `docx`, and `canvas-design` skills. Skill body is small because it delegates.

🔗 https://github.com/anthropics/skills/tree/main/skills/theme-factory

---

## 14. `skill-cleaner` — 890 tokens

The skill that audits your other skills. Reports prompt-budget usage, finds duplicates, suggests deletion candidates. This is the tool you run after installing anything from this list.

🔗 https://github.com/steipete/agent-scripts/tree/main/skills/skill-cleaner

---

## 15. `webapp-testing` — 978 tokens

End-to-end testing for live web apps using a browser harness. Includes screenshot capture, network assertions, and console error detection — in under 1000 tokens.

🔗 https://github.com/anthropics/skills/tree/main/skills/webapp-testing

---

## Patterns that keep a skill under 1000 tokens

Every skill on this list does at least one of:

1. **Delegate to references.** Long examples and recipes live in `references/*.md`, not in `SKILL.md`. The model loads them only when needed.
2. **Trust the model.** No "first, consider whether X is appropriate" preamble. Just operational instructions.
3. **Lowercase, relaxed grammar.** Capitalization and articles cost tokens. Drop them where it doesn't hurt clarity.
4. **One job per skill.** A 5,000-token skill is usually three skills wearing a trenchcoat.
5. **Prefix-locked output formats.** "Output JSON with keys X, Y, Z" beats two paragraphs of explanation.

---

## Contributing

Add an entry if it:

- Has a `SKILL.md` under 1,500 tokens (≤6,000 bytes)
- Is in a public GitHub repo
- Does one specific thing well
- Is currently maintained (push in the last 90 days)

Submit a PR with the measured byte size and a one-sentence description. Keep the existing format. No badges.

```markdown
## N. `skill-name` — XXX tokens

One sentence on what it does. One sentence on why it stays small.

🔗 https://github.com/owner/repo/path
```

---

*Maintained as part of [first-tree](https://github.com/unispark-inc/first-tree?ref=awesome-token-efficient-skills) — shared context infrastructure for agent teams.*
