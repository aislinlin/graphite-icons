---
name: graphite
description: Generate SVG icons in the Graphite Icon System style — outlined enterprise UI icons with strict geometric rules. Triggers when user asks to create, design, or generate a UI icon in Graphite style. Produces production-ready outlined SVGs (evenodd fill) at 24×24 canvas with `currentColor` for downstream recoloring. Use for single icon generation or small batches. Do NOT use for illustrations, brand marks, or non-Graphite icon systems.
---

# Graphite Icon Generator

Generates enterprise-grade UI icons following the Graphite Icon System methodology. This skill formalizes 10+ years of icon design judgment into rules that produce consistent, production-ready outlined SVGs.

## When to activate

Activate when the user explicitly asks to:
- Generate a new icon in Graphite style ("make a gear icon in Graphite")
- Design an icon following Graphite rules ("create an SVG for a battery, Graphite style")
- Show what an icon of X would look like in this system
- Batch generate multiple icons following the same rules

**Do NOT activate for**:
- General SVG editing or non-Graphite icon systems
- Illustrations, brand marks, or decorative graphics
- Requests to redesign or restyle existing icons outside Graphite

## Workflow

Follow this sequence for every icon generation request:

### Step 1 — Load rules

Read the rule files in this order:
1. `rules/01-principles.md` — 8 design principles (especially §1.4-1.8 taste rules)
2. `rules/02-geometry.md` — canvas, live area, keyline shapes
3. `rules/03-stroke.md` — stroke width, alignment, outlined production form
4. `rules/04-radius.md` — border radius grading system
5. `rules/05-angles.md` — angle rules + arrow-specific construction
6. `rules/06-naming.md` — naming convention

### Step 2 — Analyze the subject

Ask these questions IN ORDER:

1. **How many elements does this icon need?**
   - 1-2 elements → clean, no simplification needed
   - 3+ elements → §1.4 restraint activates: each element must be stylized geometrically

2. **Is there a container + content structure?**
   - Container → outlined stroke (evenodd)
   - Content → filled shapes (default per §1.6)
   - **EXCEPTION §1.6.1**: If content is a CIRCULAR APERTURE (pupil, iris, lens center) AND icon appears in REPEATED contexts (form fields, list rows, preview toggles) → use OUTLINED RING instead of solid fill
   - Example: `icn_eye` pupil is an outlined ring (r=3 outer, r=1.5 inner), not a solid dot

3. **What is the object's real-world softness?**
   - Hard-edged (house, screen) → 0px radius
   - Standard container (folder, document) → 2px radius
   - Soft object (card, wallet) → 4px radius
   - Organic (person shoulders, bell dome) → 6px radius
   - Circular by nature → full round
   - See §6

4. **Are angles constrained to 15° increments?**
   - Prefer 45° / 90° / 0° for most
   - Exception: dome curves, shoulder arcs (natural curves)
   - See §9.1

5. **Is this an arrow?**
   - Arrows use §9.2 arrow-specific rules: single filled path + square perpendicular end caps
   - Not a normal container + interior structure

6. **Would a proportional balance issue arise?**
   - Single small element below larger body → use horizontal bar, not dot (§1.7)

7. **Is this a body-like vertical form?**
   - Person torso, standing container → open bottom (§1.8)

8. **Does the main element match system visual weight?** (§1.9 — critical)
   - Single dominant shape (circle, rectangle, body) → scale to fill **12-16 units** of the 16-unit live area
   - Match up to the largest peer icons, not down
   - Example: magnifying glass lens is diameter 12 (r=6), not diameter 10 (r=5)
   - Exception: subordinate elements per §1.7 (e.g., bell clapper bar) are not "main elements"

### Step 3 — Reference existing icons

Before generating, check `reference/` for similar subjects:
- If exact subject exists, reuse or note similarity
- If similar geometry exists (e.g., asking for "envelope" and `icn_mail.svg` exists), use it as style reference
- Match the aesthetic tone of existing icons

### Step 4 — Generate SVG

Output the SVG in **production form** (outlined evenodd), not stroke source form.

**Template for outlined containers**:
```svg
<path fill-rule="evenodd" clip-rule="evenodd" d="[OUTER PATH]Z[INNER PATH]Z" fill="currentColor"/>
```

Where:
- OUTER path represents the outer visible boundary (design coords)
- INNER path is offset inward by 1.5px (stroke width)
- Outer radius (§6) determines inner radius (outer - 1.5)

**Template for interior detail fills**:
```svg
<path d="[DETAIL SHAPE]" fill="currentColor"/>
```

Or for small dots:
```svg
<circle cx="X" cy="Y" r="R" fill="currentColor"/>
```

**Full SVG wrapper**:
```svg
<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <!-- structure elements (outlined) -->
  <!-- detail elements (filled) -->
</svg>
```

### Step 5 — Name and save

Follow §11 naming convention:
- Structure: `[type]_[asset_size]?_[category]?_[description]_[visual_size]?_[thickness]?_[color]?`
- Type: `icn` for functional UI icons
- Description: objective visual (e.g., `magnifying_glass`, not `search_tool`)
- Save to a designated output folder (ask user if not specified)

### Step 6 — Present with rationale

Show the user:
1. **File location** — where the SVG was saved
2. **Design rationale** — which rules activated and why (2-4 short lines)
3. **Verification checklist** — pixel-perfect, correct radius grade, rules followed

## Output specifications

- **Format**: SVG (production form, outlined evenodd)
- **Canvas**: 24 × 24 (or 20 × 20 for status icons)
- **Color**: `currentColor` for stroke/fill (recoloring handled downstream)
- **Live area**: Icon content within 16 × 16 zone
- **Structure**: Outlined via evenodd (per §4.4)
- **Naming**: Per §11 convention

## Reference icons

The `reference/` folder contains 10 canonical icons built together with the system designer. Each demonstrates one or more Graphite rules:

| Icon | Demonstrates |
|---|---|
| `icn_folder.svg` | Standard container + diagonal tab (2px radius) |
| `icn_home.svg` | Hard-edged 0px radius, single bar for door (§1.7) |
| `icn_doc.svg` | Corner fold via outer geometry alone (§1.5) |
| `icn_photo.svg` | 3-element composition (§1.4 + §1.6 structure/detail) |
| `icn_bell.svg` | Organic 6px dome + horizontal bar clapper (§1.7) |
| `icn_mail.svg` | Container + interior V-fold detail |
| `icn_upload.svg` | Arrow single-path + square caps (§9.2) |
| `icn_download.svg` | Arrow single-path + square caps (§9.2) |
| `icn_person.svg` | Open-bottom body (§1.8) + 4px organic shoulder |
| `icn_computer.svg` | Standard 2px container + filled detail (stand) |

See `examples/CATALOG.md` for full design rationale per icon.

## Files in this skill

- `SKILL.md` — this entry file
- `rules/01-principles.md` — §1 design principles (8 rules)
- `rules/02-geometry.md` — §2-3 canvas, live area, keyline
- `rules/03-stroke.md` — §4-5 stroke width, alignment, outlined production
- `rules/04-radius.md` — §6 radius grading system
- `rules/05-angles.md` — §9 angles + arrow-specific rules
- `rules/06-naming.md` — §11 naming convention
- `reference/*.svg` — 10 canonical reference icons
- `examples/CATALOG.md` — per-icon design rationale

## Do

- ✅ Read all rule files before generating
- ✅ Check `reference/` for similar existing subjects first
- ✅ Output outlined production form (evenodd), not stroke source
- ✅ Explain which rules activated in your design rationale
- ✅ Use `currentColor` for downstream flexibility

## Don't

- ❌ Skip loading rule files ("I know the rules already")
- ❌ Generate stroke-based SVG (that's design source form, not production)
- ❌ Add decorative details to elements when 3+ elements are present (§1.4)
- ❌ Use 4px radius as default across all icons — grade it (§6)
- ❌ Use rounded end caps on internal strokes (§7)
- ❌ Guess subjects the user didn't specify (ask if ambiguous)

---

**System version**: Graphite v0.5
**Designed by**: Aislin Lin
