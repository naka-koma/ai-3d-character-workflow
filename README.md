# AI 3D Character Workflow

English | [日本語](README.ja.md)

Six agent skills for turning AI-generated character parts into editable, animated 3D models. The workflow separates reference analysis, body refinement, facial and extremity details, clothing fitting, rigging, and secondary motion.

Experiments with image-to-3D generation and Blender MCP demonstrated that the operations can be performed in sequence. Fine facial and hand geometry, joint deformation, and garment motion still had problems. These skills record both procedures and the conditions for completing or revisiting each stage.

## Skills

| Stage | Skill | Main checks |
|---|---|---|
| References and three views | [character-reference-analysis](skills/character-reference-analysis/SKILL.md) | Silhouettes, candidate joints, sides, dimensions, attachments |
| Base body | [character-base-body](skills/character-base-body/SKILL.md) | Proportions, thickness, T-pose, joint placement |
| Face, hands, and feet | [character-face-hands](skills/character-face-hands/SKILL.md) | Detailed geometry, textures, blinking, mouth opening, bends |
| Clothing and additional parts | [character-clothing-fit](skills/character-clothing-fit/SKILL.md) | Assembly that preserves anatomy, attachments, clearance |
| Rig and motion | [character-rig-motion](skills/character-rig-motion/SKILL.md) | Weights, foot IK, ground contact, walking |
| Cloth and secondary motion | [character-cloth-secondary-motion](skills/character-cloth-secondary-motion/SKILL.md) | Sway, interference, saved playback |

## Installation

With Node.js and Git available, install using the [skills CLI](https://github.com/vercel-labs/skills). Skill instructions and UI metadata are in English.

```sh
npx skills add naka-koma/ai-3d-character-workflow
```

Follow the prompts to select your agent, skills, and installation scope. To install all six skills globally for Codex:

```sh
npx skills add naka-koma/ai-3d-character-workflow --global --agent codex --skill '*' --yes
```

For a single stage, replace `--skill '*'` with `--skill character-base-body`, for example. For a project installation, run from that project's directory and omit `--global`.

To list skills without installing:

```sh
npx skills add naka-koma/ai-3d-character-workflow --list
```

### Updates

Rerun the same installation command to update the selected skills. If skills with the same names already exist, or you have edited installed copies, review differences and keep a backup before updating.

### Claude Code plugin

As with yomiyasu, a marketplace entry provides all six skills as one plugin. Run these commands inside Claude Code:

```text
/plugin marketplace add naka-koma/ai-3d-character-workflow
/plugin install ai-3d-character-workflow@ai-3d-character-workflow
```

Invoke a skill with a name such as `/ai-3d-character-workflow:character-base-body`. See [Claude Code plugin management](https://code.claude.com/docs/en/discover-plugins) for updates.

### Manual installation

You can also copy the required `skills/<skill-name>/` folders into your agent's skill directory, or read each `SKILL.md` as a production guide without installing it.

## Usage

For example, ask Codex:

```text
Use $character-base-body to check this body's proportions and T-pose.
Save unclothed front/side views and comparisons of small joint bends.
```

You do not need to execute every stage at once. Return to the stage responsible for a visual or deformation problem. The [production workflow](docs/workflow.md) describes stage relationships, and [lessons from experiments](docs/lessons.md) records observations behind the skills. These supporting documents are currently in Japanese.

## Scope and validation

The skills are not limited to a particular character or 3D generation model. Ears and tails are additional parts. SAM and OpenPose assist with region and joint estimation; their output alone does not establish a 3D skeleton or natural deformation.

This repository contains skills and documentation. It does not include generation implementations, model weights, character images, 3D assets, or experiment caches. Supply the tools needed by your chosen stages separately.

Skill structure and CLI discovery/installation are checked; see the [installation validation record](docs/installation-validation.md) for coverage. The complete workflow has not yet been rerun on a new character, and Unity Generic/Humanoid behavior remains untested.

## License

[MIT License](LICENSE) applies to the skills and documentation in this repository. Check the separate licenses of external models, tools, references, and assets used in production.
