---
name: character-clothing-fit
description: Assemble generated clothing, shoes, hair, ears, tails, and other parts around a validated base body. Use when checking attachments, placement, clearance, static silhouettes, and interference during small movements.
---

# Fit clothing and additional parts while preserving the body

## Baseline and assembly

- Use a checked body, part definitions, generated parts, and reference images as inputs. Adjust clothing and part positions, orientation, dimensions, and internal clearance around the body baseline. Do not routinely collapse anatomical thickness to force the body inside clothing.
- Keep body, clothing, and shoes separately editable. Define hair, ears, and tails as character-specific parts and record their attachment to the shared Humanoid skeleton. Do not assume every character has animal ears or a tail.
- Before and after importing into Blender, check origins, coordinate systems, the basis for real-world scale, bounds, and materials. Preserve previous versions and source assets. Follow part definitions when choosing mirrored or separately generated left/right parts.
- Check garment thickness and body clearance from front, side, and back. Specify parenting and required follow targets rather than merely hiding seams. Do not change facial geometry, expressions, or UVs without authorization to accommodate another part.

## Small-motion checks

Within the requested scope, freeze representative poses such as lowered arms, bent elbows, a lowered pelvis, or a lifted foot. Capture clothing-on/off comparisons. Record static appearance separately from motion interference.

Helper bones and corrective shapes can be useful, but define poses and ranges where they apply. If removing knee penetration requires inflating the hem substantially, include silhouette degradation in the result. Reduced penetration alone does not establish a successful correction.

If fitting requires large bulges or folds, review the original garment shape, clearance, topology, and weights. Do not respond by thinning the body further.

## Outputs and completion scope

Save editable assembly data, reference-to-part mappings, attachment locations and parenting, fixed-pose comparison images, and interference/silhouette findings.

Separate prototype completion into `static fitting`, `small-motion checks`, and `secondary cloth motion`. For requested physical motion trials, use $character-cloth-secondary-motion when available.
