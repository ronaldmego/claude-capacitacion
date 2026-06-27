# claude-guide

> A ready-to-use, **Spanish-language** enablement kit for rolling out **Claude** in
> a company — primarily **Claude Code** (technical / data), with a secondary track
> for **Cowork** (non-technical). Curated official sources, a session plan, and
> copy-paste `CLAUDE.md` / `settings.json` templates.

## The problem

Most Claude onboarding material is in English and scattered across docs, videos and
social posts. Teams that want to adopt Claude well — especially non-English-speaking
ones — end up starting from scratch and improvising the security and configuration
parts.

## The solution

This kit curates the **official sources**, organizes them by audience (technical vs
business), proposes a **training plan**, and ships **ready-to-copy templates** so a
team goes from "we have Claude" to "we use it well and safely" fast. The content is in
**Spanish on purpose**: there's plenty in English, far less curated in Spanish.

It is organized into **two self-contained tracks by audience** plus a **shared core**,
with a central router that sends each reader to the track they care about. The emphasis
is on the **Code / data track** (this repo is mostly visited by coders and data folks);
the **BPO / Cowork track** is secondary, there for whoever also wants it.

## Repository structure

```
claude-guide.md   ← central router / curated index — START HERE
README.md         ← this file (structure + table of contents)

comun/            ← shared core (used by BOTH tracks)
  seguridad.md                      🔒 dedicated security section (proven practices)
  global-claude-md-empresa.md       global CLAUDE.md template (~/.claude/)
  proyecto-claude-md-empresa.md     per-project CLAUDE.md template
  settings-json-empresa.md          settings.json sample (protect secrets)
  diagrama-capas-claude-empresa.md  layered-setup diagram (handout)

code-data/        ← Code / data track (PRIMARY) ★
  guia-code.md    Claude Code · skills · hooks · subagents · MCP · analytics

bpo/              ← BPO / Cowork track (secondary)
  guia-bpo.md     Claude Cowork for non-technical roles (Legal, HR, ops)
```

## Table of contents / Índice de contenidos

**▶ Start here:** [`claude-guide.md`](claude-guide.md) — central router: the two tracks,
shared skill/plugin sources, minimum cross-track reading, security note, and the
training program.

**🔒 Security (cross-track):** [`comun/seguridad.md`](comun/seguridad.md) — dedicated
security section: least-privilege + human-in-the-loop, secrets hygiene, and **proven
technical guardrails** (`settings.json` deny, hooks, the secret-leak guard recipe). One
of the most common questions in any rollout.

**★ Track Code / data** (primary)
- [`code-data/guia-code.md`](code-data/guia-code.md) — Claude Code, `CLAUDE.md` / skills
  / hooks / subagents / MCP, self-service analytics, project setup, security
  (secrets & permissions). Self-contained.

**Track BPO / Cowork** (secondary)
- [`bpo/guia-bpo.md`](bpo/guia-bpo.md) — Claude Cowork for non-technical roles (Legal,
  HR, ops), official sources by function, security (access & actions). Self-contained.

**Shared core — `comun/`** (used by both tracks)
- 🔒 [`comun/seguridad.md`](comun/seguridad.md) — **dedicated security section**:
  least-privilege + human-in-the-loop, secrets hygiene, and proven technical guardrails
  (deny rules, hooks, the secret-leak guard recipe).
- [`comun/diagrama-capas-claude-empresa.md`](comun/diagrama-capas-claude-empresa.md) —
  ASCII diagram of the layered setup (global vs per-project), infographic-style.
- [`comun/global-claude-md-empresa.md`](comun/global-claude-md-empresa.md) — ready
  template: **global** `CLAUDE.md` (goes in `~/.claude/`).
- [`comun/proyecto-claude-md-empresa.md`](comun/proyecto-claude-md-empresa.md) — ready
  template: **per-project** `CLAUDE.md` (repo root).
- [`comun/settings-json-empresa.md`](comun/settings-json-empresa.md) — ready sample:
  `settings.json` with a `deny` rule to protect secrets.

## Quick start

```bash
git clone https://github.com/ronaldmego/claude-guide.git
```

1. Read **[`claude-guide.md`](claude-guide.md)** (central router) and pick your track:
   - Technical / data → **[`code-data/guia-code.md`](code-data/guia-code.md)** (the primary track).
   - Business / non-technical → **[`bpo/guia-bpo.md`](bpo/guia-bpo.md)**.
2. Copy [`comun/global-claude-md-empresa.md`](comun/global-claude-md-empresa.md) → `~/.claude/CLAUDE.md` and replace `[nombre de la empresa]`.
3. Copy [`comun/proyecto-claude-md-empresa.md`](comun/proyecto-claude-md-empresa.md) → a `CLAUDE.md` at the root of each repo.
4. Copy the `settings.json` from [`comun/settings-json-empresa.md`](comun/settings-json-empresa.md) (most useful on shared / less-trusted machines).

## The layered model

A company Claude setup is built in **layers** — from the most general (every employee)
to the most specific (one repo). See
[`comun/diagrama-capas-claude-empresa.md`](comun/diagrama-capas-claude-empresa.md) for
the full diagram:

- **Layer 1 · global** (`~/.claude/CLAUDE.md` + `settings.json`) — corporate identity,
  security and generic working principles. Shareable with anyone.
- **Layer 1.5 · global skills** (`~/.claude/skills/`) — reusable skills invocable as
  `/<name>` from any project, wired from a versioned hub repo. See the global template.
- **Layer 2 · per project** (`<repo>/CLAUDE.md`) — context, commands, conventions.
- **Determinism** lives in hooks; **repeatable procedures** live in skills.

## Language

The content is in **Spanish** (the differentiator). This README is in English for
discoverability.

## License

MIT — see [LICENSE](LICENSE).
