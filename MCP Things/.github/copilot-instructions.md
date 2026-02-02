# AI Developer Workflow & Standards (Boris Cherny Style)

## 1. Core Principles
- **Reliability over Speed:** Use the smartest models (e.g., Opus 4.5/thinking models) by default. A correct slow answer is faster than a wrong fast answer.
- **Distributed Cognition:** Treat the AI as a fleet of specialized workers. Each task should have its own context/session.
- **The "Correction Tax":** Every hallucination charges human attention. Optimize instructions to eliminate repetitive errors.
- **Plan First, Execute Second:** Never start coding without an agreed-upon plan.

## 2. The Planning Protocol
- **Mode:** Always start in "Plan Mode."
- **Verification:** Before implementing, the AI must provide a structured plan:
  1. What to do.
  2. The order of operations.
  3. Why this approach was chosen.
- **Constraint:** Do not execute changes until the human explicitly approves the plan. Once approved, aim for "one-shot" implementation.

## 3. Shared Context & Knowledge (CLAUDE.md Pattern)
- **Living Document:** This file is the project's long-term memory.
- **Error Logging:** When the AI makes a mistake or suggests an anti-pattern, immediately record the fix here. 
- **Learning from PRs:** During code review, if a better pattern is identified, update these instructions so the AI "learns" the project's evolving standards.

## 4. Automation & Slash Commands
- **Atomic Workflows:** Create specific commands (or sub-agents) for:
  - `/simplify`: Review the code just written and reduce complexity.
  - `/verify`: Run end-to-end tests and validate the current change.
  - `/commit-push-pr`: Automate the boilerplate of git status, descriptive commits, and PR creation.
- **Bash Hooks:** Use `PostToolUse` hooks to run `lint` or `format` automatically after any file edit to prevent CI failures.

## 5. Development Standards
- **Isolation:** Work in separate git checkouts for parallel tasks to avoid workspace conflicts.
- **Verification Loops:** "The most important thing." Every feature must include a step where the AI verifies its own work against the project's test suite or a local dev server.
- **Tooling Access:** Ensure the AI has access to:
  - CLI tools (GitHub CLI, AWS, etc.) for real-world feedback.
  - Permissions to run safe, common commands (e.g., `npm test`) without constant prompting.

## 6. Project-Specific Constraints
- [Insert specific tech stack rules here, e.g., "Use Bun for all scripts"]
- [Insert naming conventions]
- [Insert common pitfalls to avoid]