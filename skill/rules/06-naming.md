# Rules: Naming Convention

Graphite naming follows Apple SF Symbols structural logic, adapted for enterprise UI.

**Names must be**:
- Intuitive at first read
- Extensible across variants
- Objective in describing the visual (NOT the function)

---

## Structural pattern (7 fields)

```
[type]_[asset_size]?_[category]?_[description]_[visual_size]?_[thickness]?_[color]?
```

Fields marked `?` are optional. Only `type` and `description` are always required.

**Full example**: `icn_32_toolbar_microphone_sm_fill_red`
**Minimum example**: `icn_microphone`

## Field details

| # | Field | Required | When to use | Values |
|---|---|---|---|---|
| 1 | `type` | ✅ | Always | `icn` (icon), `img` (illustration — out of Graphite scope) |
| 2 | `asset_size` | ❌ | Only when non-24 | `20`, `32`, `48`, `64` |
| 3 | `category` | ❌ | Only for scope-restricted icons | `toolbar`, `sidebar`, `slidebar`, `status` |
| 4 | `description` | ✅ | Always | Objective visual name |
| 5 | `visual_size` | ❌ | Non-standard drawing size | `sm`, `md`, `lg` |
| 6 | `thickness` | ❌ | Non-default weight or fill state | `light`, `bold`, `fill` |
| 7 | `color` | ❌ | Status / colored icons | `red`, `green`, `blue`, `orange`, `grey` |

## Description rules

- Use OBJECTIVE visual names, not functional
- Reference SF Symbols vocabulary where possible
- Exception: universally recognized functional symbols (media controls: `play`, `pause`, `stop`) may use functional names

Examples:
- ✅ `icn_magnifying_glass` (visual, universal)
- ❌ `icn_search_tool` (functional, internal jargon)
- ✅ `icn_arrow_down_to_line` (visual — arrow points down to a line)
- ❌ `icn_download` for the visual variant (use `arrow_down_to_line`); `icn_download` may be used for a functional-only descriptor if universally clear

## Naming principles

1. **Describe the object itself** — `icn_brush`
2. **Numbers precede noun** — `icn_2person` (two people)
3. **Mark directionality** — `icn_arrow_down_to_line`
4. **Mark category** — `icn_doc_text` (document with text)
5. **Shape before element** — `icn_hexagon_exclmark` (hexagon containing exclamation)
6. **Badge suffix** — `icn_person_badge_plus`
7. **Use proper nouns** — `icn_namespace`

## Status icons (sub-pattern)

```
icn_[asset_size]?_status_[description]_[color]
```

**Examples**:
- `icn_status_checkmark_green`
- `icn_20_status_exclmark_red`
- `icn_status_hourglass_grey`
- `icn_status_pause_grey`

**Status color tokens**:
- green: `#129453`
- red: `#D13535`
- grey: `#ADB1B5`

---

## Reserved words

| Position | Reserved |
|---|---|
| type (1) | `icn`, `img` |
| asset_size (2) | `20`, `24`, `32`, `48`, `64` |
| category (3) | `toolbar`, `sidebar`, `slidebar`, `status` |
| visual_size (5) | `sm`, `md`, `lg` |
| thickness (6) | `light`, `bold`, `fill` |
| color (7) | `red`, `green`, `blue`, `orange`, `grey` |

Do NOT use these tokens as free-form description terms.

---

## Good vs bad naming

| ✅ Good | ❌ Bad | Why |
|---|---|---|
| `icn_magnifying_glass` | `icn_search_tool` | Visual, not functional |
| `icn_32_microphone` | `icn_24_microphone` | 24 is default, don't label |
| `icn_status_checkmark_green` | `icn_success` | Describe visual, not meaning |
| `icn_2person` | `icn_person_2` | Numbers precede noun |
| `icn_hexagon_exclmark` | `icn_exclmark_hexagon` | Shape before element |
