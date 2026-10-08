---
name: character-face-hands
description: Refine character faces, eyes, eyelids, mouths, hands, and feet. Use when validating detailed geometry and textured blinking, mouth opening, or finger and foot deformation.
---

# Align detailed geometry, surfaces, and movement

Movement alone does not complete faces or extremities. Check reference-aligned static shape and deformation that preserves intended surface appearance.

## Inputs and method selection

- Confirm requested regions, reference expressions, textures and UVs, and required movements. Do not rebuild unrequested face, hand, or foot regions as part of the same task.
- Distinguish generated surface noise from usable eyes, noses, lips, or fingers. Choose among separate part generation, local modeling, retopology, and existing parts approved by the user. Do not assume splitting generation always improves quality.
- For blinking, establish eyeball/eyelid boundaries and the closed-eye silhouette. Check penetration into the eyeball, see-through surfaces, and painted eyes that remain visible when closed.
- For mouth opening, provide upper/lower lips, the mouth rim, and interior depth appropriate to the required motion. Include teeth and tongue only as needed. A stretched surface hole or movement of a painted mouth does not establish a working mouth.
- For hands, check separated fingers, their bases and joints, and palm thickness. For feet, check the ankle connection. Do not assert unseen fingers or anatomy inside shoes without evidence.

## Deformation and texture validation

Inspect original mesh, UVs, materials, and shape keys in Blender before local edits, and save a new version. Find shader nodes by type and check the current API.

Compare neutral, intermediate, and maximum motion with textures and geometry inspection shading. Capture unilateral and bilateral blinks, closed/open mouth, and requested finger or foot bends from useful angles. Record UV stretching, misalignment with painted eyes or mouths, and gaps in closed states.

Label clay-only checks as `geometry only`. If surface appearance and geometric boundaries disagree, return to geometry, UVs, and texture alignment before adding more movements.

## Deliverables

Save editable parts, expression or motion comparisons, changed shape keys/bones/UVs, generation inputs, and remaining problems. When delivering an export, reimport it and check the same expressions. Distinguish the range where blinking and mouth opening look natural from untested ranges.
