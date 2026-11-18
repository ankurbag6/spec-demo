<!--
Sync Impact Report
- Version change: (unversioned template) → 1.0.0
- Modified principles: none (initial adoption)
- Added principles:
  - I. TypeScript on Node
  - II. Every Feature Has Tests (NON-NEGOTIABLE)
  - III. No Secrets in Code (NON-NEGOTIABLE)
  - IV. Keep It Simple
- Template's fifth principle slot dropped: user input defines four principles.
- Added sections: Technology Constraints, Development Workflow, Governance
- Removed sections: none
- Follow-up TODOs: none
-->

# spec-demo Constitution

## Core Principles

### I. TypeScript on Node

- All application and test code MUST be written in TypeScript and run on Node.js.
- TypeScript `strict` mode MUST be enabled; `any` is allowed only with an inline comment
  explaining why.
- Plain JavaScript files are permitted only for tool configuration that cannot be TypeScript.

Rationale: one language and one runtime keep the codebase uniform and let the type checker
catch errors before tests or users do.

### II. Every Feature Has Tests (NON-NEGOTIABLE)

- Every feature, bug fix, and behavior change MUST ship with automated tests that exercise it.
- Tests MUST pass locally and in CI before a change is merged.
- A bug fix MUST include a test that fails without the fix.
- Untested code MUST NOT be merged; removing a test requires stating why in the change
  description.

Rationale: tests are the only durable proof that a feature works and keeps working.

### III. No Secrets in Code (NON-NEGOTIABLE)

- API keys, tokens, passwords, private keys, and connection strings MUST NOT appear in source
  files, tests, fixtures, commit history, or logs.
- Secrets MUST be supplied at runtime via environment variables or a secret manager.
- `.env` files MUST be git-ignored; a `.env.example` with placeholder values MAY be committed.
- A secret that is committed MUST be treated as leaked: rotate it, then remove it.

Rationale: anything committed to a repository should be assumed public eventually.

### IV. Keep It Simple

- Choose the simplest design that satisfies the current spec; do not build for speculative
  requirements (YAGNI).
- New dependencies, abstractions, or layers MUST be justified by a concrete present need.
- Prefer the Node.js standard library and small, focused modules over frameworks when either
  would work.
- Added complexity MUST be recorded and justified in the plan's Complexity Tracking section.

Rationale: simple code is easier to test, review, secure, and change.

## Technology Constraints

- Language: TypeScript (strict mode).
- Runtime: Node.js, an active LTS release.
- Testing: a single test runner chosen per project and used consistently for all tests.
- Configuration and secrets: environment variables only (see Principle III).

## Development Workflow

- Each feature follows the Spec Kit flow: specify → plan → tasks → implement.
- Every plan MUST pass a Constitution Check against Principles I–IV before implementation.
- Before merge, a change MUST: type-check cleanly, pass all tests, and contain no secrets.
- Reviewers MUST reject changes that violate a principle without a documented justification.

## Governance

- This constitution supersedes other project practices; where they conflict, it wins.
- Amendments are made by editing this file with a stated rationale and a version bump.
- Versioning follows semantic versioning:
  - MAJOR: a principle is removed or redefined incompatibly.
  - MINOR: a principle or section is added or materially expanded.
  - PATCH: clarifications and wording fixes with no change in meaning.
- Compliance is checked at plan time (Constitution Check) and at review time for every change.

**Version**: 1.0.0 | **Ratified**: 2026-11-18 | **Last Amended**: 2026-11-18
