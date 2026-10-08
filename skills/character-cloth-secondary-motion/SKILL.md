---
name: character-cloth-secondary-motion
description: Trial secondary motion for character clothing, hair, ears, and tails using helper bones, corrective shapes, or cloth simulation. Use when checking stability, interference, saved playback, and export limitations.
---

# Trial secondary motion and state its usable scope

## Method selection

Confirm baseline body/clothing, validated primary motion, references, and final use. Do not try to repair major penetration already present in primary motion through secondary movement alone.

Choose helper bones, pose-dependent corrective shapes, or physics to suit the purpose. When the user intends a physics trial, actually simulate it and distinguish failed computation or a switch to authored motion. Ears and tails need not use the same physics settings as clothing.

## Cloth physics trials

- Inspect the Blender API, scene, and modifier order; save a pre-simulation version. For dense generated meshes, consider a low-resolution simulation proxy and motion transfer.
- Define proxy thickness, mesh quality, initial body intersections, pin regions, gravity, stiffness, mass, damping, and collision distances. State whether self-collision is used. Match values to units and geometry; do not treat past settings as universal.
- Evaluate progressively from small primary motions, checking sway amplitude, hem height, rolling, body contact, and numerical divergence. Verify that transfer binding actually succeeded.
- Avoid applying body-follow deformation and physical deformation twice during transfer. If clothing collapses, isolate initial intersections, pinning, proxy geometry, and stiffness. Hold inputs and motion fixed when comparing settings.

## Unstable results

Preserve raw results. Attenuation, smoothing, and amplitude limits are prototype options, not proof of successful physics. Corrected results do not inherit any collision guarantees of the original solver.

When the same instability repeats, stop ineffective parameter changes, record the cause, and return to a stable version. Do not hide unfinished physics behind a claim of natural cloth motion.

## Saving and validation

Compare identical poses with and without secondary motion for silhouette and contact. A forward-ray coverage check cannot establish intersection behavior in every direction. State inspection directions, poses, and frame counts.

Save physics settings, raw caches, adopted results, correction methods, images, and recomputation/playback instructions. Reopen the saved file and verify reproducible motion. Distinguish live physics from animation-specific baking.

For shape-key or similar baking, record file size, memory, normals, and reuse with other motions. Dense per-frame morphs may serve validation without being a lightweight game-ready structure. Do not guarantee runtime compatibility when Unity has not been tested.
