<!-- markdownlint-disable MD013 -->
# agent-davi

Portable orchestration framework for specification-first product development.

`agent-davi` provides the core templates, policies, and contracts for running Davi as a two-stage orchestrator across different repositories.

## What Davi Is

Davi is an orchestration layer that separates product work into two mandatory stages:

1. Refiners (specify, analyze, decide)
2. Executors (implement approved work)

Davi prevents implementation drift by enforcing explicit gates, human approvals, and traceability before coding begins.

## Objectives

The project is designed to:

- Standardize how teams refine requests before implementation.
- Enforce one clear intake path per request: `Q&A`, `RCA`, or `New Implementation`.
- Require human confirmation for the identified flow before progression.
- Keep canonical agent rules in one source of truth.
- Keep project-specific knowledge inside each consumer repository.
- Improve delivery quality through SDD artifacts, approval gates, and lint evidence.

## Repository Structure

```text
templates/davi-orchestrator/
  core/                      # Canonical Davi assets owned by agent-davi
    knowledge/packs/         # Cross-project rules and shared knowledge packs
  consumer/                  # Consumer-facing templates only
    project-knowledge/
  prompts/                   # Base orchestrator prompt
  workflow/                  # Routing, knowledge gate, and governance policies
  refiners/                  # Business, architecture, governance refinement layer
  executors/                 # E1..E6 execution profiles and contracts
  sdd/                       # Six-stage SDD protocol and templates
```

## Core Principles

- Core vs consumer boundary is strict.
- No silent scope changes.
- No execution without approved refinement outputs.
- Knowledge Gate always runs before path selection.
- Path classification is explicit and single-choice.
- Human-in-the-loop approval is mandatory at critical gates.

## How To Import Davi Into Your Project

Use `agent-davi` as your canonical template source, then keep only project-specific knowledge in the consumer repository.

### 1. Add Davi templates to your repository

Choose one strategy:

- Copy the `templates/davi-orchestrator/` folder into your repo.
- Or track `agent-davi` as a git submodule/subtree and consume templates from there.

### 2. Create local project knowledge folders

In the consumer repository:

```text
.davi/project-knowledge/business/
.davi/project-knowledge/architecture/
.davi/project-knowledge/governance/
```

Use this template as reference:

- `templates/davi-orchestrator/consumer/project-knowledge/structure.template.md`

### 3. Set Davi as orchestrator prompt

Start from:

- `templates/davi-orchestrator/prompts/davi.base.prompt.md`

Then wire your runtime/tooling to always route calls through Davi.

### 4. Enforce workflow policies

At minimum, adopt these policy files:

- `workflow/routing-rules.md`
- `workflow/intake-paths.policy.md`
- `workflow/knowledge-gate.policy.md`
- `workflow/two-stage.policy.md`
- `workflow/repository-boundary.policy.md`

### 5. Run SDD for implementation paths

For `RCA` and `New Implementation`, use the 6-stage SDD sequence and approvals under:

- `templates/davi-orchestrator/sdd/`

### 6. Keep ownership boundaries clear

- Update core rules only in `agent-davi`.
- Keep consumer project knowledge only in the consumer repository.
- Promote local knowledge to core only after formal human approval.

## Typical Request Lifecycle

1. Trigger Davi.
2. Run Knowledge Gate.
3. Classify one path (`Q&A`, `RCA`, or `New Implementation`).
4. Confirm the selected path with human approval.
5. Execute refinement or handoff according to approved gates.

## Versioning and Updates

When updating Davi templates:

- Document what changed and why.
- Indicate impact level (`major`, `minor`, `patch`) when relevant.
- Provide migration notes for consumer repositories.

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for contribution workflow, quality gates, and PR expectations.
<!-- markdownlint-enable MD013 -->
