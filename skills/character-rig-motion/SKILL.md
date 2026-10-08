---
name: character-rig-motion
description: Fit rigs and skin weights to a character's reference pose, then progressively validate joint bends, foot IK, ground contact, and walking. Use when preparing motion and handoff for Generic or Humanoid workflows.
---

# Validate a skeleton and motion fitted to the body

## Rig prerequisites

Confirm references, the validated body, rest pose, body/clothing separation, target engine, and required movements. Inspect the Blender connection, scene, and API; preserve previous versions and existing actions.

Fit bones to actual shoulders, elbows, wrists, hips, knees, and ankles rather than forcing a fixed-size template onto the mesh. Use image landmarks as aids and check 3D axes, bone roll, side labels, and depth. Do not check a T-pose solely by whether arms are horizontal.

## Progressive tests

- Check neutral pose and local shoulder, elbow, knee, and ankle bends for volume preservation and weight continuity. Match maximum bone influences and normalization to the target engine.
- Define foot IK position/orientation, knee poles, and stretch behavior. If straight legs prevent a stable solution, consider an initial bend or rest-pose adjustment and inspect evaluated bones and meshes. Calibrate initial values and pole angles to this rig; do not copy trial values unchanged to other rigs.
- Expand the range through small tests appropriate to the request, such as pelvis lowering, alternating foot lifts, then walking. Distinguish stance and swing feet. During stance, measure world-space sliding, sole height, and foot IK error. Explain units in relation to foot travel and body height.
- For natural walking, consider stance/swing phases, pelvis movement, vertical bob, lateral weight transfer, arm swing, and heel/toe roll. Do not call a prototype driven by simple periodic functions a completed natural walk. Record whether reference motion was used.

## Assessment and return paths

Check both contact measurements and front/side appearance. Inspect with clothing hidden to separate body deformation from clothing interference. Return excessively thin arms or collapsed joints to body/weight correction; return large hem bulges to clothing fitting.

## Saving and engine handoff

Save the editable rig, motion clips, comparison images, contact measurements, and unresolved issues. For GLB/FBX exports, reimport and verify that IK and other constraints were baked in the required form. Distinguish playback animation from editable controls.

Bone names or counts alone do not guarantee Generic/Humanoid support. If Unity validation is requested, actually test avatar setup, bone mapping, rest pose, and motion. Record these as untested when not performed.
