# Reference Icon Catalog

10 canonical Graphite icons built collaboratively with the system designer. Each demonstrates one or more rules and serves as ground truth for future generation.

Reference these icons FIRST when generating a similar subject.

---

## `icn_folder`
- **Radius grade**: 2px (standard container)
- **Elements**: 1 (single continuous shape with tab + body)
- **Rules demonstrated**: §1.3 rounded corners, §4.4 outlined production form
- **Notes**: Diagonal 45° transition from tab to body

## `icn_home`
- **Radius grade**: 0px (hard-edged, house is structural)
- **Elements**: 2 (house outline + door bar)
- **Rules demonstrated**: §1.7 door as vertical bar (not dot), §6 hard-edged 0px
- **Notes**: Roof angle ~30° (compromise for house proportions)

## `icn_doc`
- **Radius grade**: 2px (standard paper container)
- **Elements**: 1 (single outline; fold expressed by outer geometry)
- **Rules demonstrated**: §1.5 minimal expression — no interior fold line
- **Notes**: 45° folded corner via outer chamfer

## `icn_photo`
- **Radius grade**: 2px frame + full-round sun + geometric mountain
- **Elements**: 3 (frame + sun + mountain)
- **Rules demonstrated**: §1.4 restraint under composition, §1.6 structure vs detail
- **Notes**: Mountain stylized as two-peak with step (not literal); sun is single dot

## `icn_bell`
- **Radius grade**: 6px (organic dome)
- **Elements**: 2 (bell body + clapper bar)
- **Rules demonstrated**: §1.7 clapper as horizontal bar, §6 organic 6px
- **Notes**: Semi-circular dome, tall body from y=10 to y=17

## `icn_mail`
- **Radius grade**: 2px (standard envelope)
- **Elements**: 2 (envelope frame + V-fold detail)
- **Rules demonstrated**: §1.6 structure (frame) + detail (V-fold)
- **Notes**: V-fold approximated as vertical-offset chevron shape

## `icn_upload`
- **Radius grade**: N/A (arrow, no container)
- **Elements**: 2 (single-path arrow + base line)
- **Rules demonstrated**: §9.2 arrow-specific single-path + square caps
- **Notes**: Tip at (12, 4); base line at (5, 17)-(19, 18.5)

## `icn_download`
- **Radius grade**: N/A (arrow)
- **Elements**: 2 (single-path arrow + base line)
- **Rules demonstrated**: §9.2 arrow-specific rules
- **Notes**: Tip at (12, 15.06); mirror of upload but with different Y anchoring

## `icn_person`
- **Radius grade**: 6px (organic — shoulders); full round (head circle)
- **Elements**: 2 (head ring + body)
- **Rules demonstrated**: §1.8 open bottom, §6 organic 6px shoulders
- **Notes**: Body has NO bottom line; only 1.5-wide notches at (4→5.5, 20) and (18.5→20, 20)

## `icn_computer`
- **Radius grade**: 2px (screen frame)
- **Elements**: 2 (screen frame + base bar)
- **Rules demonstrated**: §1.6 structure (screen outlined) + detail (base filled)
- **Notes**: Standard container + horizontal fill for stand

## `icn_magnifying_glass`
- **Radius grade**: Full round (lens); handle uses square caps (arrow-like)
- **Elements**: 2 (lens ring + handle) — combined in single path via tangent attachment
- **Rules demonstrated**: §1.9 visual weight (lens diameter 12), §6 full round for circular, §9 45° handle
- **Notes**: Lens center (11, 11), outer r=6, inner r=4.5. Handle attaches tangentially at (14.68, 15.74) and (15.74, 14.68) — two points on outer circle 1.5 units apart (= stroke width perpendicular)

## `icn_eye`
- **Radius grade**: Organic (almond bezier curves; no rectilinear radius)
- **Elements**: 2 (eye almond outline + pupil ring) — both outlined via evenodd
- **Rules demonstrated**: **§1.6.1 exception** (aperture uses outlined ring, NOT solid fill), §1.9 visual weight (eye 16 wide × 12 tall)
- **Notes**: Pupil is an outlined ring (outer r=3, inner r=1.5), NOT a solid dot. Used for preview toggles in password fields and list rows where repeated solid dots would appear visually heavy. Almond shape uses bezier curves with points at (4, 12), (12, 6), (20, 12), (12, 18) — flatter mid-section, more tapered ends than a pure ellipse. Critical exception case demonstrating §1.6.1.

---

## How to use this catalog

When generating a new icon, follow this order:

1. **Check for exact match** — does the requested subject already exist?
2. **Check for similar geometry** — is there a reference with the same underlying shape?
   - Rectangle with rounded corners → `icn_folder`, `icn_doc`, `icn_mail`, `icn_photo`, `icn_computer`
   - Vertical body form → `icn_person`, `icn_bell`
   - Arrow → `icn_upload`, `icn_download`
   - Hard-edged geometric object → `icn_home`
3. **Match the aesthetic register** — same stroke weight, same radius grading logic, same simplification level
