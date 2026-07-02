# Rules: Design Principles

Graphite icons follow 8 principles. §1.1-1.3 define visual register. §1.4-1.8 are taste rules that resolve edge cases.

Apply principles in order when analyzing an icon subject.

---

## §1.1 Enterprise register

Target business users. Proportion and form scale to the depicted object. Avoid cartoon / Q-style aesthetics. Maintain professional, stable tone.

## §1.2 Stroke as primary language

Default stroke: **1.5px**. Do not vary stroke width for stylistic reasons.

## §1.3 Rounded corners fused with square forms

Combine rounded corners with squared elements. Roundness scales with real-world softness (see §6).

---

## §1.4 Restraint under composition (multi-element rule)

**Trigger**: Icon has **3 or more elements**.

**Rule**: Each individual element must be simplified — stylized geometry over literal representation. Cleverness lives in COMPOSITION, not in each element.

**How to apply**:
- Ask: how many distinct elements does this icon need?
- If 3+: for each element, use geometric abstraction, not literal detail
- Example: `icn_photo` has frame + mountain + sun. Mountain is stylized geometry (two peaks + step), sun is a single dot (no rays). All simplified.

## §1.5 Minimal expression (single-element rule)

**Rule**: Complexity comes from FORM, not decoration. When an element's meaning is already carried by the outer shape's geometry, do NOT add interior detail lines.

**How to apply**:
- Ask: can the meaning be read from the outer shape alone?
- If yes: do not add interior lines to "reinforce" it
- Example: `icn_doc` folded corner is expressed by the chamfered outline. No L-shaped fold indicator line is added inside.

## §1.6 Structure by stroke, detail by fill (container-content rule)

**Trigger**: Icon has a CONTAINER + INTERIOR content structure.

**Rule**:
- Structural elements (outer containers, main outlines) → **outlined via evenodd** (§4.4)
- Interior detail elements (dots, small shapes) → **solid fills**

**Rationale**: A 1.5px stroke on small interior shapes becomes visual noise at small sizes. Fills preserve shape at any scale.

**How to apply**:
- Identify: is there a container? (frame, screen, envelope, etc.)
- Interior small elements → fill, not stroke

### §1.6.1 Exception — Aperture elements use outlined ring

**Trigger**: Interior detail is a CIRCULAR APERTURE (pupil, iris, camera lens center, ring indicator) AND the icon appears in REPEATED UI contexts (password preview toggles, list rows, form inputs, table columns).

**Rule**: Use **outlined ring** (outer circle + inner circle, evenodd), NOT solid fill.

**Rationale**:
- Solid dots repeated across a row create heavy visual noise
- The aperture metaphor (eye pupil, camera iris) is inherently about a "hole" or "opening" — a ring communicates this better than a solid dot
- Rings maintain visual lightness even at high repetition density

**How to identify**:
- Ask: does the interior element represent an APERTURE / OPENING / IRIS?
- Ask: will this icon appear multiple times in a row (form fields, list items, repeated toggles)?
- If yes to both → use outlined ring per §1.6.1

**Example**: `icn_eye` for password preview — pupil drawn as outlined ring (outer r=3, inner r=1.5), not solid dot.

**Counter-example**: `icn_photo` sun — sun is not an aperture, it is a solid celestial object. §1.6 applies (solid fill), §1.6.1 does not.

## §1.7 Proportional balance (single-below-body rule)

**Trigger**: A single small element sits BELOW a larger main body.

**Rule**: Use a **horizontal bar**, NOT a dot. A single dot creates proportional imbalance against the larger mass above.

**How to apply**:
- Example: `icn_bell` clapper is a 4×1.5 horizontal bar, not a single dot.

## §1.8 Open bottom for body-like forms

**Trigger**: Icon is a VERTICAL BODY shape (person torso, standing container, shoulder-like structure).

**Rule**: Leave the bottom OPEN. Do NOT draw a closing horizontal line at the bottom. Use small connector notches at corners to join outer and inner walls.

**How to apply**:
- Example: `icn_person` body has open bottom with only 1.5-wide notches at (4→5.5, 20) and (18.5→20, 20).

**Rationale**: Reduces visual clutter at the bottom edge; shape reads as natural verticality, not sealed container.

## §1.9 Visual weight consistency (system-level rule)

**Rule**: Every icon's main element must maintain visual weight comparable to peer icons in the system. When placed side-by-side, no icon should appear noticeably smaller, lighter, or emptier than its neighbors.

**How to apply**:
- For icons whose main element is a single dominant shape (circle, rectangle, body form), scale that shape to fill **12-16 units** of the 16-unit live area
- Do not draw main elements at 8-10 unit sizes unless the metaphor strictly requires it
- The system's baseline visual weight is set by the largest peer icons — match up, not down

**Reference dimensions from existing icons**:
- `icn_folder`: 16 wide × 13 tall
- `icn_photo`: 14 × 14
- `icn_computer`: 16 × 12 (screen)
- `icn_home`: 14 × 15
- `icn_doc`: 14 × 16
- `icn_person`: head diameter 8 + body 16 wide (total ~16 tall)
- `icn_magnifying_glass`: lens diameter **12**, handle extends beyond

**Example**: A magnifying glass lens at diameter 10 (r=5) would appear lighter than peers. Correct diameter is 12 (r=6) to match system weight.

**Exception**: Elements intentionally kept small for compositional balance (e.g., the horizontal bar clapper in `icn_bell` per §1.7). These are not "main elements" — they are subordinate to the primary body.

---

## Decision order for AI

For any icon subject, evaluate in this order:

1. **Count elements** — trigger §1.4?
2. **Container structure?** — trigger §1.6 (structure vs detail)
3. **Single element under body?** — trigger §1.7 (bar not dot)
4. **Vertical body shape?** — trigger §1.8 (open bottom)
5. **Meaning already in outer shape?** — apply §1.5 (no redundant interior lines)
6. **Main element dimensioning** — apply §1.9 (fill 12-16 units to match system weight)
