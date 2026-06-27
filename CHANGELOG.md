# Changelog

All notable changes to this project are documented here.
Format based on [Keep a Changelog](https://keepachangelog.com/).

## [Unreleased]

### Added
- **Dedicated security section** → `comun/seguridad.md`. Cross-track: the common
  principle (least-privilege + human-in-the-loop, secrets only in `.env` and never
  printed) plus **proven technical guardrails** for the Code/data track — `settings.json`
  deny rules, hooks as deterministic guardrails, and a full recipe for a **secret-leak
  guard** (`PreToolUse` hook, warn mode) with the golden rule `${VAR:+PRESENTE}` (never
  `${VAR:-...}`, which prints the value). Linked from the README index, the router, and
  the Code track. Generic/public-safe; reflects real production practice. Security is one
  of the most common questions in any rollout, so it now has its own block.
- **"Global skills" layer (Layer 1.5)** in the global `CLAUDE.md` template + README
  layered model: reusable skills invocable as `/<name>` from any project, wired from a
  versioned hub repo into `~/.claude/skills/`, with secrets loaded global-first from a
  gitignored `~/.claude/.secrets/.env` and a reproducible setup script. Generic/public-safe.
- **⚠️ NO TOCAR convention** in the per-project `CLAUDE.md` template: mark off-limits
  areas (external forks, sibling apps, generated code) so the agent doesn't edit what
  looks dead but isn't.

### Changed
- **v3.1 — reorganized into folders + added a navigable table of contents.** Content is
  now grouped by track: `code-data/` (Code/data track, primary), `bpo/` (BPO/Cowork
  track, secondary), and `comun/` (shared core: the `CLAUDE.md`/`settings.json` templates
  + layered diagram, used by both tracks). The **README** now carries a **table of
  contents / índice** linking each block at its new path; `claude-guide.md` stays as the
  curated router. Files were moved with `git mv` (history preserved) and all internal
  links updated (verified: 0 broken). No content changed — only structure. This lets the
  Code/data track go as advanced as it needs (hooks, etc.) without affecting BPO readers.
- **v3.0 — split the single guide into two self-contained guides by audience plus a
  central router.** `claude-guide.md` is now the **central summary** (two tracks,
  shared skill sources, cross-track minimum reading, security note, training program).
  New `guia-code.md` (**primary** Code/data track) and `guia-bpo.md` (**secondary**
  BPO/Cowork track) are each self-contained, so a reader opens only the track they
  care about. Emphasis shifted to the Code track (this public repo is mostly visited
  by coders/data); BPO is secondary. README updated (Code-first framing, new file
  table, track-based quick start). No content lost — existing sections were moved into
  the matching track guide; shared skill-sources table and cross-track minimum reading
  stay in the central.
- Reframed the deliverables (layered diagram + 3 templates + settings sample) as
  **Code-track artifacts**: the central "Materiales" section now points to
  `guia-code.md` for the how-to and notes that BPO/Cowork uses Project instructions
  instead of `CLAUDE.md`. The diagram header now states it belongs to the Code track.

### Added
- `skills.sh` (registry/buscador web de skills) added to the shared skill-sources table
  in `claude-guide.md`, marked as discovery (review `SKILL.md` + scripts before install).
- Initial public-ready release: curated Claude enablement guide (`claude-guide.md`),
  layered-setup diagram, and ready-to-copy templates (`global` / `proyecto` `CLAUDE.md`,
  `settings.json` sample).
- English `README.md`, `LICENSE` (MIT).

### Changed
- Renamed repo `claude-capacitacion` → `claude-guide` and the main guide
  `capacitacion-claude.md` → `claude-guide.md` (clearer name); references updated.
- Content sanitized for public use: removed first-person and internal-workflow material;
  kept the generic, reusable content. Content language: Spanish (by design).
