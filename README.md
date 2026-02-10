# Agent Coordination Hub

Central coordination repository for all AI agents working in ionoi-inc.

## Quick Start for New Agents

When joining any ionoi-inc project:

1. **Read [ORG.md](ORG.md)** - Understand organizational context and operating rules
2. **Read [AGENTS.md](AGENTS.md)** - Know the team roster and delegation guidelines  
3. **Check [procedures/](procedures/)** - Review relevant workflows
4. **Review project issues** - See what work is in progress
5. **Introduce yourself** - Comment on relevant issues if coordination is needed

## Key Documents

- **[ORG.md](ORG.md)** - Organizational standards, repository rules, communication protocols
- **[AGENTS.md](AGENTS.md)** - Team roster, delegation hierarchy, handoff guidelines
- **[templates/](templates/)** - Issue templates for agent handoffs
- **[procedures/](procedures/)** - Standard operating procedures for common workflows

## Core Principles

- **ionoi-inc is home base** - All work happens in the org unless explicitly stated
- **GitHub is the coordination layer** - Issues and PRs are how agents communicate
- **Documentation is required** - Changes must be documented
- **Clear handoffs** - Use issue templates and tags

## Communication

Use GitHub issue tags for agent handoffs:
- `nebula` - Cloud agent work
- `seafloor` - Strategic decisions
- `claude` - Server/deployment
- `cursor` - Active development
- `antigravity` - IDE assistance
- `urgent`, `blocked`, `handoff` - Status flags

## Repository Structure

```
agents/
├── ORG.md              # Organizational context and rules
├── AGENTS.md           # Team roster and delegation guidelines
├── README.md           # This file
├── templates/          # Issue templates for handoffs
│   ├── handoff.md
│   ├── deployment.md
│   └── bug-report.md
└── procedures/         # Standard operating procedures
    ├── new-project.md
    ├── deployment.md
    └── pr-workflow.md
```

---

**Questions?** Open an issue with the appropriate tag.