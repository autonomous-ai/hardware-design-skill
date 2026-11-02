# Hardware design skill

Rules and a send-checklist for designing physical products that a factory will build. The rules come from a
factory's senior engineers' reviews and from their engineering guideline. They cover structure, joints, fasteners,
boards and sheet, CAD, 2D drawings and BOM. The skill works for Claude Code and Codex.

- `hardware-design/SKILL.md`: how to work, and the checklist.
- `hardware-design/references/engineering-guideline.vi.md`: the factory's full engineering guideline, in
  Vietnamese.

## Install

Claude Code:

```sh
git clone https://github.com/autonomous-ai/hardware-design-skill ~/hardware-design-skill
ln -s ~/hardware-design-skill/hardware-design ~/.claude/skills/hardware-design
```

Codex:

```sh
ln -s ~/hardware-design-skill/hardware-design ~/.codex/skills/hardware-design
```

To update, run `git -C ~/hardware-design-skill pull`.

## Use it in a product repo

Add this to the product's AGENTS.md:

> Before any design, CAD, drawing or BOM work, load the `hardware-design` skill
> (https://github.com/autonomous-ai/hardware-design-skill) and follow its checklist. If it isn't installed, read
> `hardware-design/SKILL.md` from that repo.

Keep only that product's own rules in its AGENTS.md.

## Adding a lesson

After any feedback from the factory or the team, add the lesson the same day, with its date and the case that taught
it:

- A lesson for any product goes into this checklist, by pull request.
- A lesson for one product goes into that product's AGENTS.md.
