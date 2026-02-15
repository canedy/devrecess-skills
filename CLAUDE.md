# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repo contains free, open-source narrative-driven learning skills for developers. Each skill is a SKILL.md file in the [Anthropic Agent Skills](https://github.com/anthropics/skills) format that transforms an AI assistant (Claude, ChatGPT, etc.) into an immersive learning guide with missions, comic panel visuals, and hands-on coding exercises grounded in real documentation.

## Three-Repo Architecture

| Repo | Purpose |
|---|---|
| **devrecess** | Marketing site (Hono + React + Tailwind) |
| **devrecess-skills** (this repo) | Generated Agent Skills (SKILL.md files) |
| **devrecess-engine** | Generation pipeline that produces skills |

Skills in this repo are **generated output** from the engine. Manual edits are welcome for fixing bugs or improving content, but new skills should be generated through the engine.

## Repository Structure

```
skills/
├── learn-bun-space-beginner/
│   └── SKILL.md
├── learn-bun-space-intermediate/
│   └── SKILL.md
├── learn-docker-detective-beginner/
│   └── SKILL.md
└── ...

catalog.json              # Machine-readable index of all skills
.claude-plugin/
└── marketplace.json      # Makes this repo installable as a Claude Code plugin
```

## Skill Format

Each SKILL.md follows the Agent Skills spec:

```markdown
---
name: learn-bun-space-beginner
description: Interactive narrative learning guide that teaches Bun through a Space adventure...
---

[Narrative guide content: story setup, missions, Think First questions, comic panels, etc.]
```

## Naming Convention

Skills are named: `learn-{technology}-{theme}-{difficulty}`

| Component | Values |
|---|---|
| technology | `bun`, `docker`, `kubernetes`, `mastra`, `c-cpp`, `react`, `typescript`, `nodejs`, `python`, `nextjs`, `go` |
| theme | `space`, `detective`, `rpg`, `heist`, `action-rpg` |
| difficulty | `beginner`, `intermediate`, `advanced` |

## How Users Access Skills

1. **Claude Code:** Install via `/plugin install canedy/devrecess-skills`
2. **Claude.ai:** Upload a SKILL.md to a Project's knowledge
3. **ChatGPT / Other:** Copy-paste the SKILL.md contents as the first message

## catalog.json

A machine-readable index of all skills, used by the marketing site to display the browsable grid. Contains `name`, `technology`, `theme`, `difficulty`, `description`, and `path` for each skill.

Regenerate it when skills are added or removed using the engine's batch script, or manually update it.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on:
- Requesting new technologies or themes
- Fixing issues with existing skills (outdated APIs, broken examples)
- Improving content quality
