# Rules: Border Radius (Grading System)

Border radius is **NOT** a single default value. It is a **graded system**. Each icon's radius is chosen based on the object's real-world softness.

## The 5 grades

| Radius | Register | When to use | Examples |
|---|---|---|---|
| **0px** | Hard-edged | Objects structurally sharp in real life | House (roof, walls), screen bezel, chip, monitor edge |
| **2px** | Standard | Default for most functional UI containers | Folder, document, mail, photo frame, computer screen |
| **4px** | Soft | Cushioned or handleable objects | Card, wallet, bag |
| **6px** | Organic | Body parts, dome shapes, biological forms | Person shoulders, bell dome |
| **Full round** | Circular | Shape is intrinsically circular | Dot, sun, ring, avatar |

## Decision rule

Ask: **"Would this object be sharp, cushioned, or organic if I touched it in real life?"**

- Sharp → 0px
- Everyday container → 2px
- Cushioned → 4px
- Body / dome → 6px
- Circular → full round

## Inside-align implication

Design coordinates specify OUTER radius. The inner path's radius is calculated:

**Inner radius = Outer radius - 1.5** (stroke width)

| Outer | Inner |
|---|---|
| 2px | 0.5px |
| 4px | 2.5px |
| 6px | 4.5px |
| Full round (r) | r - 1.5 |

## Do

- ✅ Grade the radius per object — don't use one default everywhere
- ✅ Use 0px for house, screen, chip — respect their hard nature
- ✅ Use 6px for person shoulders and bell dome — respect organic softness

## Don't

- ❌ Use 4px across the whole system for "friendliness" — that drifts into consumer aesthetics
- ❌ Use 2px on person shoulders — too rigid for a body form
- ❌ Use 0px on a folder — too harsh for a paper container

---

## Common mistake

Treating radius as "the default value" (2px) applied everywhere. **The default is: MATCH THE OBJECT'S NATURE.**
