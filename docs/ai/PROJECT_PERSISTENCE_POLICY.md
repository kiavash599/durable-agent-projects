# Universal Software Project Persistence Policy

## Purpose

Treat chat history and temporary model context as working memory only.

The repository, its code, and its maintained documentation are the durable and authoritative memory of the project.

Do not keep important project knowledge only in chat, hidden reasoning, temporary context, or session memory.

If information is important enough to affect future implementation, architecture, debugging, testing, security, maintenance, deployment, release behavior, handoff, interoperability, or decision-making, persist it in the repository in an appropriate durable form.

---

# 1. Core Principle

**Chat is working memory. The repository is durable memory.**

Any project knowledge that future work may depend on must be recorded in a structured, discoverable, and maintainable form inside the repository.

Do not assume that future sessions, agents, models, or human developers will have access to the current conversation.

A new contributor should be able to understand the important project state and continue the work by inspecting the repository alone.

---

# 2. Scale Documentation to the Project

Apply this policy proportionally to the size, complexity, risk, and lifecycle of the project.

Do not create unnecessary documentation structures for small or temporary projects.

For example:

- A small prototype may need only `README.md` and a short project-state note.
- A medium-sized project may need project state, decisions, design notes, and runbooks.
- A large, production, regulated, security-sensitive, or multi-agent project may require the full documentation structure described below.

Preserve the principles of durability, traceability, and maintainability, but avoid documentation overhead that provides no practical value.

---

# 3. Respect Existing Project Conventions

Before creating a new documentation file or directory:

1. Inspect the repository.
2. Identify existing documentation conventions.
3. Reuse existing authoritative files where appropriate.
4. Update existing documents instead of creating duplicate sources of truth.
5. Create a new file only when it has a clearly distinct purpose.

The filenames and directory names in this policy are recommended defaults, not mandatory names.

If the project already uses equivalents such as:

- `STATUS.md`
- `DECISIONS.md`
- `docs/decisions/`
- `docs/architecture/`
- `CONTRIBUTING.md`
- `OPERATIONS.md`

then prefer those existing conventions.

Do not create parallel documentation systems unless there is a strong reason.

---

# 4. Persist Significant Decisions

Whenever a significant technical or architectural decision is made, record it permanently.

Examples include:

- architecture choices
- framework or technology selection
- database design
- API structure
- authentication and authorization strategy
- tenant isolation
- security boundaries
- data models
- integration strategy
- deployment architecture
- infrastructure decisions
- storage strategy
- messaging or event architecture
- caching strategy
- compatibility decisions
- important implementation constraints
- important rejected alternatives
- major trade-offs
- release-process decisions

For significant architectural decisions, use an Architecture Decision Record when appropriate.

Recommended location:

`docs/architecture/adr/`

Example:

`docs/architecture/adr/ADR-001-tenant-isolation.md`

A useful ADR should normally include:

- Title
- Status
- Date
- Context
- Problem
- Decision
- Alternatives considered
- Rationale
- Trade-offs
- Consequences
- Constraints
- Related components or files
- Relevant references

Do not create ADRs for trivial implementation details.

An ADR is appropriate when changing the decision later would likely require meaningful redesign, migration, compatibility work, security review, or substantial reimplementation.

---

# 5. Maintain Current Project State

For projects where ongoing state matters, maintain a durable project-state document.

Recommended default:

`PROJECT_STATE.md`

It should describe the actual current state of the project, not a transcript of historical discussion.

Keep it updated with relevant information such as:

- completed work
- current work in progress
- partially completed work
- blocked work
- known issues
- unresolved questions
- current implementation state
- verified state
- test status
- important environment state
- next recommended actions

Do not allow the project-state document to become stale.

When the project state changes materially, update it.

---

# 6. Persist Requirements and Specifications

Do not allow important requirements to exist only in chat.

Store durable requirements and specifications in the existing project structure, or under a location such as:

`docs/specs/`

Examples:

- product requirements
- functional requirements
- API requirements
- behavioral requirements
- security requirements
- performance requirements
- compatibility requirements
- acceptance criteria
- agent responsibilities
- workflow specifications

If requirements change, update the authoritative requirement document and record any important scope, assumption, or compatibility changes.

---

# 7. Persist Technical Design

Store significant implementation and system-design knowledge in the existing documentation structure or under:

`docs/design/`

Examples:

- system architecture
- component responsibilities
- module boundaries
- interfaces
- data flows
- database relationships
- service interactions
- state machines
- background jobs
- event flows
- API behavior
- error-handling strategy
- synchronization logic
- caching strategy
- concurrency model
- security boundaries

The goal is that another engineer or AI agent can understand why the system is structured the way it is without needing access to the original conversation.

---

# 8. Persist Constraints and Assumptions

Important constraints must not remain implicit.

Record them in an appropriate existing document or under a location such as:

`docs/constraints/`

Examples:

- platform limitations
- hosting limitations
- repository or plan limitations
- external API limitations
- licensing constraints
- environment restrictions
- operating-system requirements
- performance limits
- security assumptions
- unsupported features
- compatibility requirements
- external dependencies
- temporary compromises

Also record assumptions that materially affect implementation.

If an assumption is later invalidated, update the documentation and any dependent decisions.

---

# 9. Persist Important Testing and Evidence

Important validation results should be durable when they matter to future work, audits, debugging, releases, or handoffs.

Store important evidence in the existing project structure or under:

`docs/evidence/`

When appropriate, record:

- what was tested
- test scope
- test method
- result
- relevant commit or version
- environment
- known gaps
- failed checks
- manual verification
- acceptance evidence

Avoid vague statements such as:

"Tests passed."

Prefer evidence that makes the result reproducible, understandable, or auditable.

Do not duplicate information already captured reliably by CI unless additional durable context is useful.

---

# 10. Maintain Runbooks When Operations Matter

Operational procedures that may need to be repeated should not depend on chat history.

Use existing operational documentation or a location such as:

`docs/runbooks/`

Examples:

- local development setup
- environment setup
- deployment
- release procedure
- database migration
- backup and recovery
- rollback
- troubleshooting
- service restart
- incident recovery
- secrets or configuration setup

Only create runbooks for procedures that have real reuse or operational value.

---

# 11. Track Blockers and Open Questions

For projects where unresolved issues materially affect progress, maintain them in a durable location.

Recommended default:

`BLOCKERS.md`

or use the project's existing issue-tracking system.

Record, when relevant:

- blocker
- why it blocks progress
- affected components
- evidence
- attempted solutions
- current workaround
- owner
- next action
- resolution condition

When a blocker is resolved, update or close it.

Do not leave resolved blockers appearing active.

---

# 12. Maintain Handoff Information When Needed

For long-running, multi-session, multi-agent, or collaborative work, maintain a handoff document.

Recommended default:

`HANDOFF.md`

It should make it possible for another contributor to resume work safely.

Include only relevant information such as:

- current objective
- current project state
- last completed action
- current branch or commit
- important files
- important decisions
- unresolved issues
- blockers
- current test status
- known risks
- exact next recommended action
- commands or procedures required to resume safely

Update the handoff after meaningful sessions or before transferring work to another contributor or agent.

For very small projects, a separate handoff file may not be necessary if the same information is already clear elsewhere.

---

# 13. Keep Documentation Tool- and AI-Independent

Documentation should describe the project itself, not the temporary conversation or model.

Avoid statements such as:

"Claude decided..."
"ChatGPT suggested..."
"We discussed this in chat..."

Prefer:

"Decision: PostgreSQL RLS is used for tenant isolation."

Documentation should remain useful regardless of whether the next contributor is:

- a human developer
- Claude
- Codex
- ChatGPT
- another coding agent
- an automated build or release agent

The repository must remain the source of durable project knowledge.

---

# 14. Avoid Documentation Noise

Do not persist every trivial action.

Examples that usually do not require permanent documentation:

- renaming a local variable
- formatting changes
- minor refactoring
- fixing a typo
- obvious implementation details with no architectural impact

Persist information when it may affect future:

- reasoning
- implementation
- interoperability
- security
- testing
- debugging
- maintenance
- deployment
- migration
- release behavior
- compatibility

Prefer useful documentation over excessive documentation.

---

# 15. Documentation Lifecycle

For important changes, follow this lifecycle:

Decision  
→ Persist  
→ Implement  
→ Verify  
→ Record evidence when needed  
→ Update project state  
→ Update handoff when needed

Do not consider significant work fully complete if the implementation changed but the authoritative documentation still describes the old state.

---

# 16. Conflict Between Chat and Repository

Do not automatically trust chat memory over repository documentation.

If current conversation context conflicts with repository documentation:

1. Identify the discrepancy.
2. Inspect the implementation.
3. Inspect available tests and evidence.
4. Determine the verified current state.
5. Update the authoritative documentation.
6. Do not silently rely on temporary chat memory.

The repository should converge toward verified truth.

---

# 17. Code and Tests Are Also Sources of Truth

Documentation must not contradict verified implementation.

When determining current behavior, consider:

- source code
- automated tests
- schemas
- configuration
- migrations
- CI results
- deployment configuration
- existing authoritative documentation

Documentation should explain important intent, rationale, constraints, and state that cannot be inferred reliably from code alone.

Do not duplicate the entire implementation in prose.

---

# 18. Preserve Traceability for Important Changes

When a decision materially affects implementation, keep enough traceability to connect the decision to the relevant code, specification, or evidence.

Where useful, reference:

- source files
- modules
- issues
- pull requests
- commits
- tests
- ADRs
- specifications

Do not over-link trivial changes.

---

# 19. Keep Documents Maintainable

Do not dump raw chat transcripts into project files.

Convert conversation content into structured project knowledge.

Prefer:

- facts
- decisions
- rationale
- constraints
- consequences
- evidence
- current state
- next actions

over conversational history.

Documentation should be concise enough to remain readable and complete enough to preserve important project knowledge.

---

# 20. Session Durability Check

Before ending any meaningful work session, perform a durability check.

Ask internally:

**"If this conversation disappeared now, would any important project knowledge be lost?"**

Check at minimum:

1. Were significant architectural decisions made?
2. Were important technical decisions made?
3. Did requirements change?
4. Were new constraints discovered?
5. Were assumptions added or invalidated?
6. Did architecture or technical design change?
7. Were important tests or validations completed?
8. Was new evidence produced?
9. Did a new blocker appear?
10. Was a blocker resolved?
11. Did the project state materially change?
12. Does handoff information need updating?
13. Would another contributor need information from this conversation to continue safely?

If yes, persist the relevant information before treating the work as complete.

---

# 21. Recommended Structure

Use the existing repository structure whenever possible.

If no suitable structure exists and the project is complex enough to justify it, use or adapt:

```text
/docs
  /architecture
    /adr
  /design
  /specs
  /constraints
  /evidence
  /runbooks
  /agents

PROJECT_STATE.md
HANDOFF.md
BLOCKERS.md
CHANGELOG.md
README.md
```

Not every project needs every file or directory.

Create only what provides durable value.

---

# 22. Multi-Agent Projects

If the project uses multiple AI agents, consider maintaining durable agent documentation under:

`docs/agents/`

Document important items such as:

- responsibilities
- role boundaries
- permissions
- interaction contracts
- escalation rules
- required inputs
- required outputs
- ownership boundaries
- handoff rules

Do not rely on one agent's private context to coordinate the system.

Shared project knowledge must be available in the repository.

---

# 23. Verification Rule

Never claim that important project knowledge has been persisted unless the relevant repository file was actually created or updated.

When practical:

1. inspect the final file,
2. verify that the new information is present,
3. verify that it does not contradict implementation or other authoritative documents,
4. verify that duplicate sources of truth were not introduced.

---

# 24. Default Behavior

Unless explicitly instructed otherwise:

- inspect existing documentation before creating new documentation,
- update existing authoritative records when possible,
- persist significant decisions and discoveries as part of the work,
- keep project state synchronized with implementation,
- avoid dependence on chat memory,
- avoid unnecessary documentation overhead.

Do not wait for the user to explicitly request documentation every time a significant project decision is made.

Documentation of important project knowledge is part of completing the work.

---

# Final Rule

**Do not rely on chat history as permanent project memory.**

Use chat for temporary reasoning, interaction, and coordination.

Use the repository for durable project knowledge.

If losing the current conversation would cause important project decisions, rationale, state, constraints, evidence, recovery information, or implementation context to disappear, that information has not yet been persisted properly.
