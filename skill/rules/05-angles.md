# Rules: Angles + End Caps + Arrow-Specific Construction

## §9.1 General angle rule

- **Base unit**: 15°
- **Most common angle**: 45°
- **Allowed angles**: 15°, 30°, 45°, 60°, 75°, 90° (and their mirrored equivalents)
- **Forbidden**: arbitrary angles that don't snap to 15° increments

**Rationale**: Constraining angles to a shared unit means all diagonal elements across the system feel like they belong to one family.

**Exception**: natural curves (dome tops, shoulder arcs, keyline arcs) are not "angles" — they are radius-based. The 15° rule applies to STRAIGHT LINE segments.

## End caps

- **Internal stroke end caps**: **square (butt cap)** — never rounded
- **Outer container corners**: follow §6 radius grading

The outer boundary may be rounded per §6. **Internal strokes** (text lines, dividers, interior details) **always terminate with square end caps**.

---

## §9.2 Arrow-specific construction (CRITICAL)

Arrows in Graphite follow a specific pattern that differs from other icons.

### Structure

**Arrow = ONE filled path** combining head + shaft, NOT separate elements.

The chevron head and shaft are traced as one continuous closed outline.

### End caps on chevron arms

- **Square cut, perpendicular to arm direction**
- NOT slanted, NOT rounded
- The "cap" segment connects the outer edge endpoint to the inner edge endpoint via a perpendicular line

### Angles

- Chevron arms typically at 45°
- Shaft is vertical (90°)

### Template for arrow (single path)

For an arrow pointing DOWN with tip at `(12, y_tip)`, shaft top at `(11.25/12.75, y_top)`:

Coordinates derive from geometry:
- Shaft width: 1.5 (from 11.25 to 12.75)
- Chevron arm at 45°: perpendicular thickness 1.5
- Perpendicular offset per axis = 1.5 / √2 ≈ 1.06

**Reference example** (`icn_download`):
```svg
<path d="M12 15.06L17.03 10.03L15.97 8.97L12.75 12.19V4H11.25V12.19L8.03 8.97L6.97 10.03L12 15.06Z" fill="currentColor"/>
```

Path traversal:
1. `M 12 15.06` — arrow tip
2. `L 17.03 10.03` — outer edge of right chevron arm
3. `L 15.97 8.97` — square perpendicular end cap
4. `L 12.75 12.19` — inner edge of right chevron arm, ends at shaft
5. `V 4` — shaft right side up to top
6. `H 11.25` — shaft top edge
7. `V 12.19` — shaft left side down
8. `L 8.03 8.97` — inner edge of left chevron arm
9. `L 6.97 10.03` — square perpendicular end cap
10. `L 12 15.06` — back to tip
11. `Z` close

### Key coordinates for 45° chevron with 1.5px thickness

At any tip position `(x_tip, y_tip)`:
- Perpendicular offset per axis: `1.5 / √2 ≈ 1.06`
- The perpendicular cap segment is: `Δx = ±1.06, Δy = ∓1.06`

---

## Base line pattern

Many arrows include a horizontal "base line" (destination or source line).

**Standard base line dimensions**: 
- Length: 14 (from x=5 to x=19)
- Thickness: 1.5 (from y=17 to y=18.5 for arrows at bottom of icon)

**Template**:
```svg
<path d="M5 17H19V18.5H5V17Z" fill="currentColor"/>
```

---

## Do

- ✅ For arrows, always use single filled path (head + shaft merged)
- ✅ Use square perpendicular end caps on chevron arms
- ✅ Keep chevron arms at exactly 45°

## Don't

- ❌ Draw arrow head and shaft as separate paths
- ❌ Use slanted or rounded end caps on chevron arms
- ❌ Use arbitrary chevron angles (only 45° or other 15° increments)
