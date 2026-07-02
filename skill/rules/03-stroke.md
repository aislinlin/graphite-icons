# Rules: Stroke (Width, Alignment, Production Form)

## Stroke width

- **Default**: 1.5px
- **Exception**: 1px permitted ONLY when a shape is very small or interior detail is so dense that 1.5px would collapse the icon
- **Interior consistency**: interior lines use the same weight as the outline. Never mix weights within one icon.

## Stroke alignment (production-critical)

**Graphite strokes are conceptually INSIDE-aligned.**

- Design coordinates represent the OUTER visible boundary
- Strokes live entirely INSIDE that boundary

### Why inside-align matters

1. Center-aligned 1.5px strokes straddle pixel boundaries → half-pixel anti-aliasing → visible blur
2. Center-align makes visible outer radius = design + 0.75 = 2.75px (not the intended 2px)
3. Inside-align guarantees pixel-perfect rendering and exact designed radius

### Production form

Because SVG does not natively support `stroke-alignment: inside`, Graphite outputs SVGs as **outlined paths using evenodd fill**:

- **Outer path** = the OUTER visible boundary (design coordinates)
- **Inner path** = the outer boundary offset INWARD by 1.5px (the stroke width)
- Both paths combined with `fill-rule="evenodd"` fill the 1.5px ring between them

**This is not optional. Every Graphite structural element is output in this outlined form.**

---

## Templates

### Template: Outlined container (rounded rectangle)

For a rounded rectangle from `(x, y)` to `(x+w, y+h)` with outer radius `r`:

```
Outer path: M(x+r,y) H(x+w-r) A r r 0 0 1 (x+w,y+r) V(y+h-r) A r r 0 0 1 (x+w-r,y+h) H(x+r) A r r 0 0 1 (x,y+h-r) V(y+r) A r r 0 0 1 (x+r,y) Z
Inner path: same shape offset inward by 1.5px, inner radius = r - 1.5
```

**Example (2px outer, 0.5px inner)**:
```svg
<path fill-rule="evenodd" clip-rule="evenodd" d="M6 5H18A2 2 0 0 1 20 7V15A2 2 0 0 1 18 17H6A2 2 0 0 1 4 15V7A2 2 0 0 1 6 5ZM6 6.5H18A0.5 0.5 0 0 1 18.5 7V15A0.5 0.5 0 0 1 18 15.5H6A0.5 0.5 0 0 1 5.5 15V7A0.5 0.5 0 0 1 6 6.5Z" fill="currentColor"/>
```

### Template: Outlined circle (ring)

For circle at `(cx, cy)` with outer radius `R`:

```svg
<path fill-rule="evenodd" clip-rule="evenodd" d="M(cx+R) (cy)A R R 0 1 0 (cx-R) (cy)A R R 0 1 0 (cx+R) (cy)ZM(cx+R-1.5) (cy)A (R-1.5) (R-1.5) 0 1 0 (cx-R+1.5) (cy)A (R-1.5) (R-1.5) 0 1 0 (cx+R-1.5) (cy)Z" fill="currentColor"/>
```

### Template: Filled detail (interior element)

```svg
<path d="[shape]" fill="currentColor"/>
```

Or for small circular dots:
```svg
<circle cx="X" cy="Y" r="R" fill="currentColor"/>
```

---

## Two forms of Graphite SVG

- **Canonical form** (design source): 1.5px stroke SVG. Used for design iteration, editing.
- **Production form** (output): outlined evenodd SVG. Used for publishing, matches inside-align rendering.

**Graphite skill outputs Production form directly.** Never emit stroke source form as the final result.

---

## Stroke construction order (design phase)

When designing (not applicable to AI generation, but relevant to explain rationale):

1. Solid strokes before dashed
2. Left to right, top to bottom
3. Outer to inner (wrap-inward)
4. Center-align on pixel axis
