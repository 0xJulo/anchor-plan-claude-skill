# Anchor Plan

A Claude Code skill that walks you through planning and architecting Solana Anchor programs before writing any code.

## What it does

`/anchor-plan` runs an interactive planning session that covers:

- **Program purpose** — clarifies goals and objectives
- **Users & actors** — identifies who interacts with the program and how
- **Account design** — defines state, fields, types, space, and relationships
- **PDA strategy** — maps seeds, bump handling, and derivation patterns
- **Instructions** — designs each instruction with context, validations, state changes, and events
- **Error handling** — anticipates failure modes and defines custom errors
- **Access control** — determines signers, authority, upgrade strategy, and invariants

At the end, it produces a structured program plan as a markdown file you can use to build from.

## Install

Clone this repo and copy the `.claude/skills/anchor-plan` folder into your project's `.claude/skills/` directory:

```
your-project/
└── .claude/
    └── skills/
        └── anchor-plan/
            ├── SKILL.md
            └── plan-template.md
```

## Usage

In Claude Code, run:

```
/anchor-plan
```
