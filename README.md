# Durable Agent Projects

A reusable governance and project-memory framework for software repositories maintained by humans and AI coding agents.

## Why this exists

Chat history is temporary. A repository is durable.

Important decisions, constraints, implementation state, verification evidence, blockers, and handoff context should live with the project—not only in a conversation that future contributors may never see.

This repository provides two complementary documents:

- **`CLAUDE.md`** — repository-level working rules for Claude Code, covering investigation, implementation, verification, safety, Git discipline, and durable project knowledge.
- **`docs/ai/PROJECT_PERSISTENCE_POLICY.md`** — a tool-independent policy for keeping project knowledge discoverable, current, and useful to humans and AI agents.

Although the entry file is named `CLAUDE.md`, the persistence principles are intentionally model-independent and can be adapted for Codex, ChatGPT, Claude, or other coding agents.

## Repository structure

```text
.
├── CLAUDE.md
├── LICENSE
├── README.md
└── docs/
    └── ai/
        └── PROJECT_PERSISTENCE_POLICY.md
```

The path above is intentional: `CLAUDE.md` imports the policy from `docs/ai/PROJECT_PERSISTENCE_POLICY.md`.

## Using it in a project

1. Copy `CLAUDE.md` to the root of your repository.
2. Copy `PROJECT_PERSISTENCE_POLICY.md` to `docs/ai/`.
3. Review the project-specific sections in `CLAUDE.md`.
4. Replace the example runtime, test, and repository-map entries with verified details from your project.
5. Scale the documentation practices to the project's size, risk, and lifecycle.

## What the policy promotes

- Inspecting the existing system before modifying it
- Acting autonomously when intent is clear
- Keeping changes focused and reversible
- Verifying work with real evidence
- Preserving security and compatibility
- Recording significant decisions and project state
- Maintaining useful handoff information
- Treating repository code, tests, and documentation as durable memory

## Adapting for other agents

For an agent that reads a different instruction filename, copy or translate the relevant governing rules into that agent's supported entry file while keeping the persistence policy at the documented path.

Avoid maintaining divergent copies. Choose one authoritative policy and have agent-specific entry files reference it.

## Scope

These documents are a starting point, not a substitute for project-specific engineering judgment. Existing architecture, security requirements, contribution rules, and verified repository conventions should remain authoritative.

## License

Released under the [MIT License](LICENSE).

