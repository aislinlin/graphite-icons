# Changelog

All notable changes to Graphite Icon System are documented here.

Format: [Semantic Versioning](https://semver.org/). Pre-1.0 releases indicate draft / in-development status.

---

## [0.7] — 2026-07-07

### Added
- **§4.5 Sub-pixel polish** (Optional / Advanced) — manual polish technique for symmetric 1.5px stroke edge rendering. NOT applied by skill by default. Reference example in `icn_battery` polished version.
- Reference research: technique is industry-niche, not documented in Material Icons / Feather / Lucide / IBM Carbon.

### Rationale
- Preserves skill's auto-generation simplicity
- Documents craft-level knowledge without over-engineering the ruleset
- Signals designer's depth without forcing overly complex generation rules

## [0.6] — 2026-07-02

### Added
- **§1.6.1 Aperture exception** — Circular apertures (pupil, iris) in repeated UI contexts use outlined ring instead of solid fill
- **§1.9 Visual weight consistency** — System-level rule: main elements fill 12-16 units to match peer icons
- 2 canonical reference icons: `icn_magnifying_glass`, `icn_eye`
- Skill workflow Step 8 (visual weight check) and Step 2 §1.6.1 exception branch

### Changed
- Total canonical reference set: 10 → 12 icons

## [0.5] — 2026-07-02

### Added
- **§1.4** Restraint under composition (3+ elements)
- **§1.5** Minimal expression (form over decoration)
- **§1.6** Structure by stroke, detail by fill
- **§1.7** Proportional balance (bar not dot)
- **§1.8** Open bottom for body-like forms
- **§4.4** Stroke inside-align + outlined production form
- **§6** Border radius grading (0 / 2 / 4 / 6 / full round)
- **§9.2** Arrow-specific construction (single filled path + square caps)
- Status color tokens
- "Deliberate" tagline

### Changed
- Emoji policy: only ✅ ❌ ⚠️ retained
- Overview restructured into "What it is / Why it exists"

## [0.4] — 2026-06-26

### Added
- Complete naming convention (§11 with 8 subsections)
- Status icon sub-pattern
- Reserved words table
- Good vs bad naming examples

## [0.3] — 2026-06-26

### Added
- System named "Graphite"
- Bilingual (EN + Traditional Chinese) draft for author review

## [0.2] — 2026-06-26

### Changed
- Restructured to big-brand documentation format (Material / Carbon / HIG style)
- Stroke Logic explanation clarified
- End caps distinction (internal vs container) added

## [0.1] — 2026-06-26

### Added
- Initial synthesis from personal knowledge base
