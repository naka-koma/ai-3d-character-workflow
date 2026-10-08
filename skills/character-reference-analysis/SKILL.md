---
name: character-reference-analysis
description: Analyze character references and front, side, and back views to define generation parts, silhouettes, candidate joints, dimensions, and attachment points. Use when turning SAM masks or OpenPose landmarks into production part definitions.
---

# Define parts and placement from references

Produce part definitions for generation and assembly. Do not treat 2D estimates as a finished 3D structure.

## Inputs and analysis

- Confirm source images, front/side/back correspondence, shared character features, and outfit. Do not mix different designs or outfits. Mark unseen regions as estimates.
- Use SAM-family tools for regions and OpenPose or similar tools for candidate image-space joints. Check available tools and models; do not report extraction as executed when it was not.
- Overlay masks, landmarks, and labels on source images for visual review. State whether left/right labels use character or image coordinates. Distinguish animal ears from human ears and tails from hair. Do not automatically confirm anatomy hidden by clothing or detections that misread stylized artwork.
- Do not assume three views describe an identical shape. Align reference height and centerlines, and record conflicting silhouettes or joint locations. Record pixels and normalized values for 2D measurements; justify coordinate systems and units for 3D dimensions.

## Part definition output

Record each part in machine-readable JSON with linked images. Include `part_id`, category (shared anatomy / character-specific / clothing), reference images and visible regions, side and symmetry, candidate dimensions, orientation, attachment location, candidate target bones, generation unit, evidence, and unresolved details.

Mark silhouettes, joints, and attachment points individually as `observed`, `estimated`, or `unknown`. Bone assignments are candidates and do not establish Humanoid compatibility. Link images and masks so later stages can reuse the same inputs.

## Completion and return path

Complete this stage when every generation target is linked to references and its side, orientation, and missing views can be reviewed. For unclear parts, limit the prototype scope or specify additional references needed. Do not absorb contradictory silhouettes through extreme 3D deformation.

Hand off body thickness and deformation checks to $character-base-body when available.
