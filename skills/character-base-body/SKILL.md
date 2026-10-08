---
name: character-base-body
description: Align a generated character base body with reference proportions, T-pose, and joint locations. Use when checking anatomy, thickness, and basic deformation without clothing before fitting generated parts.
---

# Establish body proportions and deformable anatomy

Use the unclothed body as the baseline. Do not force anatomy inside an outfit.

## Work

- Confirm the body asset, references, generation provenance, pose, units, and forward/up/left/right axes. Respect the user's choice of existing bodies or external assets. Do not turn one character's preference against external bodies into a universal ban.
- Before operating Blender, inspect the connection and scene and save a new version. Preserve existing work and check the current Blender API and enum values before changes.
- Inspect front, side, and oblique views for head-to-body proportions, shoulder width, torso thickness, pelvis, and the lengths and cross sections of upper arms, forearms, thighs, and lower legs. Preserve anatomical thickness under clothing.
- When aligning a T-pose, check shoulder, elbow, wrist, hip, knee, and ankle locations as well as horizontal arms. OpenPose landmarks provide placement clues; they do not determine depth or joint axes.
- Focus smoothing, seam repair, and retopology on regions that need to move. Evaluate mesh closure separately from anatomically plausible, deformation-ready shape.

## Validation

Capture before/after images with the same camera and lighting. Check the unclothed neutral pose and small shoulder, elbow, knee, and ankle bends. Create a temporary test rig only as needed. Record collapsed cross sections, inverted bends, displaced joints, and left/right differences.

If arms become excessively thin, shoulders compressed, or joints collapsed, return to body shape or reference alignment. Do not thin the body further to avoid clothing contact. Follow the reference and user intent when judging acceptable proportions and stylization.

## Outputs and completion

Save the baseline body, comparison images, measurements and coordinate system, candidate joints, shape changes, and unresolved regions. Track `generated`, `static shape checked`, and `joint deformation checked` as separate states.

Proceed to clothing fitting after proportions and joint placement match the references and the requested small bends show no major failures. State the tested motion range; do not guarantee movements outside it.
