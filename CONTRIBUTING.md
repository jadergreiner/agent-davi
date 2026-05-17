<!-- markdownlint-disable MD013 -->
# Contributing to agent-davi

Thank you for contributing to `agent-davi`.

This repository defines canonical orchestration assets used by multiple consumer projects. Changes here can have broad impact, so please follow this workflow carefully.

## Scope and Ownership

`agent-davi` owns:

- Core orchestration rules
- Workflow policies
- Refiner/Executor contracts
- Shared canonical knowledge packs
- SDD and handoff templates

Consumer repositories own:

- Project-specific knowledge under `.davi/project-knowledge/*`
- Local constraints, evidence, and implementation details

Do not move consumer-specific runtime knowledge into this repository unless formally approved.

## Contribution Types

Typical accepted contributions:

- Clarity improvements in orchestration docs
- Policy consistency fixes
- New templates for refinement/execution governance
- Contract updates for executor profiles
- Rule catalog updates with traceable rationale

## Branch and Commit Guidelines

- Use focused branches (one topic per branch).
- Use Conventional Commits, for example:
  - `feat(davi): add mandatory flow confirmation gate`
  - `docs(readme): improve consumer import guide`
  - `fix(policy): align routing and knowledge gate wording`

Keep commits scoped and explain rationale in the commit body when policy behavior changes.

## Required Quality Gates

Before opening a PR:

1. Ensure paths and references are valid after your changes.
2. Run markdown lint on changed docs.
3. Verify no unintended files were modified.
4. Confirm the change respects core vs consumer boundary policy.

## Rule Changes

If you add or modify a rule in the rule catalog:

1. Update the catalog with a new incremental ID.
2. Add impacted artifacts.
3. Keep wording testable and operational.
4. Align related policy/prompt/template files in the same PR.

## Pull Request Checklist

Include in your PR description:

- Problem statement
- Proposed change
- Impacted files
- Compatibility notes for consumer repositories
- Any required migration steps

For behavior changes, include a short before/after example.

## Review Expectations

Reviewers will prioritize:

- Policy consistency across files
- Operational clarity
- Backward compatibility for consumers
- Traceability of decisions and gates

## Security and Safety

- Do not commit secrets.
- Do not include project-specific private data from consumer repos.
- Keep examples generic and reusable.

## Need Help?

Open an issue with:

- Context
- Desired outcome
- Current behavior
- Suggested direction (if available)

Thank you for helping keep Davi reliable and reusable across projects.
<!-- markdownlint-enable MD013 -->
