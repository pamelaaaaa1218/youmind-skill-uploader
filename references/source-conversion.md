# Converting an existing Skill for YouMind

The source Skill already defines the behavior. Convert its packaging for a single YouMind instruction field without redesigning the capability.

## Accepted sources

- A complete `SKILL.md` directory
- A standalone `SKILL.md`
- A complete source prompt
- An existing YouMind draft supplied by the user
- A GitHub repository or file that the user identifies as the source

Resolve the exact source before publishing. Do not scan a folder and choose a different Skill merely because its files are easier to access.

## Compilation rules

1. Remove YAML frontmatter and Agent-interface metadata from the instruction value.
2. Keep the operational body of `SKILL.md`.
3. Read every file explicitly required by the operational body. Inline only the instructions needed at runtime.
4. Replace local cross-references such as `Read references/foo.md` with the relevant content or a self-contained rule. The YouMind version must not depend on inaccessible local paths.
5. Exclude tests, eval reports, changelogs, Git history, GitHub publishing notes, installation instructions, and maintenance-only comments.
6. Preserve protected source prompts byte-for-byte when the user requests exact preservation, including punctuation, placeholders, and line breaks.
7. Do not silently add capabilities, tools, guarantees, or policies absent from the source Skill.
8. When the source requires another installed Skill or current Agent capability, describe the capability generically unless the dependency's exact public name is essential.
9. If essential referenced content is missing, stop rather than publishing an incomplete or invented instruction.

## Fidelity check

Before filling the form, compare the compiled instruction with the source and verify:

- the same trigger and task boundary;
- the same required inputs and outputs;
- the same protected prompt text;
- the same safety and quality constraints;
- no unresolved local file paths;
- no maintenance-only material in the public instruction.
