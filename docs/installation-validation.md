# Installation validation

Checked on Windows on 2026-10-08.

- All six `SKILL.md` files passed the skill-creator structural validator.
- Skill instructions and UI metadata were checked for English text. UI descriptions meet the 25–64 character length requirement.
- `npx skills add . --list` discovered the six expected skills.
- An isolated temporary home was used to install all six skills for Codex and Claude Code with `--global --skill '*' --yes --copy`. Repeating the command succeeded. All 24 installed skill/metadata files matched their source files.
- The documented Codex flags also succeeded without `--copy` in a separate temporary home.
- `claude plugin validate` passed for both the marketplace manifest and the plugin manifest.
- README links and Git whitespace were checked. The Japanese README was reviewed with yomiyasu's linter and meaning-difference checker; repeated procedural sentence endings were retained where natural.

These checks cover packaging, discovery, and file installation. They do not establish runtime invocation of the Claude Code plugin, successful character production, or Unity Generic/Humanoid compatibility. External generation tools and Blender MCP are not installed by this package.
