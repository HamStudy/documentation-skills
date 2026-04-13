# Documentation Skills

A collection of agent skills for technical documentation work.

## Skills

| Skill | Description |
|-------|-------------|
| [documentation](skills/documentation/) | Write, structure, review, and reformat technical documentation using the Diátaxis framework |
| [accessible-technical-writing](skills/accessible-technical-writing/) | Write, review, and edit educational content explaining technical concepts to non-technical audiences |

## Installation

Install individual skills using the skills CLI:

```bash
# Install the documentation skill
npx skills add <repo-url>@documentation
```

Or install all skills in this repository:

```bash
npx skills add <repo-url>
```

## About This Repository

This repository contains agent skills compatible with [skills.sh](https://skills.sh/) and the broader Agent Skills ecosystem. Skills follow the open [Agent Skills specification](https://agentskills.io/specification).

Each skill is a self-contained directory with a `SKILL.md` file and optional supporting files in `references/`, `scripts/`, or `assets/`.

## Repository Structure

```
.
├── README.md                          # This file - project overview
└── skills/
    ├── documentation/                 # Individual skill directory
    │   ├── SKILL.md                   # Skill definition (required)
    │   └── references/                # Supporting documentation
    └── accessible-technical-writing/  # Educational content for non-technical audiences
        ├── SKILL.md
        └── references/
```

## License

See individual skills for license information.
