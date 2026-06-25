# Changelog

All notable changes to this project are documented here.
Format based on [Keep a Changelog](https://keepachangelog.com/).

## [Unreleased]

### Changed
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
