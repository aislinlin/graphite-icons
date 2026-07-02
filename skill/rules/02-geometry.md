# Rules: Geometry (Canvas, Live Area, Keylines, Gaps)

## Canvas

- **Size**: 24 × 24 px (default) OR 20 × 20 px (status icons)
- **ViewBox**: `0 0 24 24` (or `0 0 20 20`)

## Padding (safe area)

- **Value**: 4px on all sides
- **Implication**: Icon coordinates live within (4, 4) to (20, 20)

## Live area

- **Size**: 16 × 16 px maximum
- **Rule**: No icon shape may extend beyond this zone
- **Rationale**: Guarantees optical consistency across the system

**Common mistake**: Using the full 24 × 24 canvas as drawable area. This causes visual weight inconsistency.

## Keyline shapes (optical balance)

Shapes with equal pixel dimensions have different perceived weights. Adjust bounding sizes:

| Shape | Keyline size |
|---|---|
| Circle | 16 × 16 px |
| Square | 14 × 14 px |
| Rectangle (portrait) | 12 × 16 px |
| Rectangle (landscape) | 16 × 12 px |

**Rationale**: A 16 × 16 square appears heavier than a 16 × 16 circle to the eye. Shrinking squares restores balance.

## Gaps

- **Minimum**: 1.5px between adjacent shapes
- **Rule**: Never less than 1.5px. Increase for clarity, never decrease.
- **Purpose**: Preserves shape distinction at 16px display size.

**Example**: Two person icons overlapping — 1.5px gap between them ensures they read as two distinct figures.

---

## Templates

**SVG wrapper (24×24)**:
```svg
<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <!-- structure and detail elements -->
</svg>
```

**SVG wrapper (20×20, status icons)**:
```svg
<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
  <!-- typically: filled circle background + white interior element -->
</svg>
```
