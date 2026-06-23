# claude-capacitacion

> A ready-to-use, **Spanish-language** enablement kit for rolling out **Claude** in
> a company — both Enterprise / Cowork (non-technical) and Claude Code (technical).
> Curated official sources, a session plan, and copy-paste `CLAUDE.md` /
> `settings.json` templates.

## The problem

Most Claude onboarding material is in English and scattered across docs, videos and
social posts. Teams that want to adopt Claude well — especially non-English-speaking
ones — end up starting from scratch and improvising the security and configuration
parts.

## The solution

This kit curates the **official sources**, organizes them by audience (business vs
technical), proposes a **training plan**, and ships **ready-to-copy templates** so a
team goes from "we have Claude" to "we use it well and safely" fast. The content is in
**Spanish on purpose**: there's plenty in English, far less curated in Spanish.

## What's inside

| File | What it is |
|---|---|
| **`capacitacion-claude.md`** | **The guide** — curated official sources (BPO/Cowork + Code/data), a 3-session training plan, security by track, and a communication-style model. **Start here.** |
| `diagrama-capas-claude-empresa.md` | ASCII diagram of the layered setup (global vs per-project), infographic-style. |
| `global-claude-md-empresa.md` | Ready template: **global** `CLAUDE.md` (goes in `~/.claude/`). |
| `proyecto-claude-md-empresa.md` | Ready template: **per-project** `CLAUDE.md` (repo root). |
| `settings-json-empresa.md` | Ready sample: `settings.json` with a `deny` rule to protect secrets. |

## Quick start

```bash
git clone https://github.com/ronaldmego/claude-capacitacion.git
```

1. Read **`capacitacion-claude.md`** (the guide) — from its index you reach the diagram and the templates.
2. Copy `global-claude-md-empresa.md` → `~/.claude/CLAUDE.md` and replace `[nombre de la empresa]`.
3. Copy `proyecto-claude-md-empresa.md` → a `CLAUDE.md` at the root of each repo.
4. Copy the `settings.json` from `settings-json-empresa.md` (most useful on shared / less-trusted machines).

## The layered model

A company Claude setup is built in **layers** — from the most general (every employee)
to the most specific (one repo). See `diagrama-capas-claude-empresa.md` for the full
diagram:

- **Layer 1 · global** (`~/.claude/CLAUDE.md` + `settings.json`) — corporate identity,
  security and generic working principles. Shareable with anyone.
- **Layer 2 · per project** (`<repo>/CLAUDE.md`) — context, commands, conventions.
- **Determinism** lives in hooks; **repeatable procedures** live in skills.

## Language

The content is in **Spanish** (the differentiator). This README is in English for
discoverability.

## License

MIT — see [LICENSE](LICENSE).
