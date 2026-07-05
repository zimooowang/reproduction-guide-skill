# Reproduction Guide Skill

`reproduction-guide` is a Codex skill for creating evidence-driven reproduction guides for machine learning papers, models, benchmarks, datasets, and open-source research projects.

It is designed for cases where a user wants more than a paper summary: the output should define what is actually reproducible, map public evidence to implementation components, expose unknowns, and end with a concrete first action.

## What It Does

- Builds a reproducibility boundary from public evidence.
- Classifies the project type before choosing modules to analyze.
- Avoids assuming RL, agents, rollouts, rewards, verifiers, SFT, or distributed training unless the project actually uses them.
- Maps official artifacts, related papers, and third-party code into an engineering plan.
- Splits reproduction into levels from "run released artifacts" to "research-grade training reproduction".
- Audits generated guides for unsupported claims and over-specific assumptions.
- Tailors a full guide to the user's compute, time, codebase, and skill constraints.

## Workflow

The skill follows an A/B/C workflow:

1. **Full map**: generate a complete evidence-driven reproduction guide.
2. **Audit**: remove unsupported claims, missing validation, and category assumptions.
3. **Tailor**: convert the full guide into an executable plan for the user's actual constraints.

The final tailored output should end with exactly one first action: a file, command, expected output, and success flag.

## Installation

Copy this folder into your Codex skills directory:

```bash
cp -R reproduction-guide ~/.codex/skills/
```

Then invoke it explicitly:

```text
Use $reproduction-guide to create an evidence-driven reproduction guide for this paper or open-source ML project.
```

## Repository Layout

```text
reproduction-guide/
├── SKILL.md
├── README.md
└── agents/
    └── openai.yaml
```

## Example Prompts

```text
Use $reproduction-guide to build a reproduction guide for this paper. Focus on what can be reproduced with one 24GB GPU.
```

```text
Use $reproduction-guide to audit this reproduction plan and remove unsupported assumptions.
```

```text
Use $reproduction-guide to tailor the full reproduction plan to my current repo and hardware.
```

## License

Add an open-source license before publishing if you want others to reuse, modify, or redistribute this skill.
