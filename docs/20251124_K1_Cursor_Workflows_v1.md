# Cursor Workflows v1
**File:** 20251124_K1_Cursor_Workflows_v1.md  
**Owner:** ~K¹  
**Purpose:** Reusable, named workflows for the Cursor Agent and other AI models to follow when executing common tasks on Kyle’s machine.

Each workflow is a **playbook**: a numbered list of steps.  
When a user asks for that workflow, follow the steps in order unless clearly inappropriate.

---

## 0. How to use these workflows

- When the user describes a task that matches one of these workflows, you should:
  1. Identify the closest matching workflow by name and description.
  2. Inform the user which workflow you intend to follow.
  3. Execute the steps, adapting only where necessary to fit the actual repo.

- If multiple workflows apply:
  - Choose the **simplest** one that solves the problem.
  - Or propose combining them and explain how.

- If no workflow matches closely:
  - Use these as references to design an ad-hoc plan.
  - Consider creating a new workflow (in explanation) that the user could add to this file later.

---

## 1. Workflow: Full TypeScript / JS error cleanup

**Goal:** Clean up TypeScript/JS build errors in a project.

**Steps:**

1. Ask the user which command is used to check for errors:
   - Example: `npm run build`, `npm run lint`, `tsc`, etc.

2. Run the command (if tools are enabled and safe to use).

3. Collect the first few errors:
   - Capture error messages, file paths, and relevant lines.

4. Group errors by type:
   - Missing types / imports
   - Type mismatches
   - Undefined variables
   - Config issues

5. Propose a strategy:
   - “We’ll fix type mismatches first, then missing imports, then config.”

6. Fix errors category by category:
   - Edit the smallest region of code necessary.
   - Avoid broad type `any` unless explicitly allowed by the user.

7. Re-run the error command after each category:
   - Confirm that specific errors are resolved.
   - Do not introduce new ones unnecessarily.

8. When command passes:
   - Summarize changes.
   - List patterns to avoid in the future.

---

## 2. Workflow: Add a new feature (web/backend)

**Goal:** Implement a new feature request with tests.

**Steps:**

1. Clarify requirements:
   - Inputs, outputs, scenarios.
   - Edge cases, performance constraints, and any UX expectations.

2. Locate relevant code:
   - Search by keywords.
   - Identify controllers/handlers/components/services involved.

3. Propose a design:
   - Describe updates to:
     - APIs/routes.
     - State management.
     - Components or services.
   - Suggest where tests should live.

4. Implement:
   - Create/update functions or components.
   - Wire up routes/endpoints as needed.
   - Respect established architecture.

5. Add or update tests:
   - Unit tests for new logic.
   - Integration/e2e tests if part of existing practice.

6. Run tests:
   - Use the project’s standard test command(s).
   - Fix failing tests related to the changes.

7. Summarize:
   - Files changed.
   - New entry points / routes.
   - How to exercise the feature manually.

---

## 3. Workflow: Large refactor without breaking everything

**Goal:** Refactor a large area (module, package, subsystem) safely.

**Steps:**

1. Understand the existing design:
   - Identify the module boundary.
   - Find any docs/diagrams.
   - Scan for implicit contracts (public interfaces, widely used functions).

2. Propose a refactor plan:
   - Phase 1: reorganize structure (move/split/rename).
   - Phase 2: adjust internals for clarity/performance.
   - Phase 3: cleanup (dead code, comments, docs).

3. Present the plan to the user:
   - Ask for approval before large changes.

4. Execute Phase 1:
   - Move files and adjust imports.
   - Ensure builds/tests still pass.

5. Execute Phase 2:
   - Improve logic, naming, and structure.
   - Keep changes localized and cohesive.

6. Execute Phase 3:
   - Remove obsolete code.
   - Update docs and READMEs.
   - Add comments where behavior is non-obvious.

7. Run full tests/build:
   - Fix any regressions.

8. Summarize:
   - Explain the new structure.
   - Point out any potential future work left for later.

---

## 4. Workflow: Documentation synthesis from code

**Goal:** Generate or update documentation based on the code in a repo.

**Steps:**

1. Identify the audience:
   - Developer getting started?
   - Maintainer?
   - Ops/DevOps?

2. Scan the repo for existing docs:
   - `README`, `docs/` folder, `*spec*.md`, `*design*.md`.

3. Build an outline:
   - What problem the project solves.
   - Architecture overview.
   - Key components/modules.
   - How to run, test, and deploy.

4. Fill in sections by reading code:
   - Use function/class names, comments, file structure.
   - Avoid copying huge blocks of code; describe behavior.

5. Propose where to place docs:
   - `README.md` for overview.
   - `docs/` for deeper guides.

6. Create or update docs files with the synthesized content.

7. Summarize:
   - Mention new/updated files.
   - Suggest future documentation improvements.

---

## 5. Workflow: Investigate and explain an unfamiliar repo

**Goal:** Rapidly understand a new codebase and explain it to the user.

**Steps:**

1. Identify entry points:
   - `main` / `index` / `app` files.
   - Framework-specific entry points.

2. Scan structure:
   - Top-level directories.
   - Notable modules (auth, db, api, ui, etc.).

3. Look for docs:
   - `README`, `docs/`, comments.

4. Build a mental model:
   - What is the system’s purpose?
   - What are the major subsystems?
   - How does data flow?

5. Present a summary:
   - 1–2 paragraphs + bullet list of major components.
   - Highlight unclear parts and open questions.

6. Ask user what they care about:
   - Performance?
   - Features?
   - Bugs?

7. Focus subsequent exploration on those concerns.

---

## 6. Workflow: Safe configuration change

**Goal:** Change a configuration (env, deployment, feature flags) safely.

**Steps:**

1. Identify which config file(s) matter:
   - `.env`, `config/*.yml`, `.json`, framework-specific config.

2. Find any related docs:
   - Project docs.
   - External docs for framework/tool.

3. Propose change:
   - What key value(s) will change.
   - Potential impacts (performance, security, UX).

4. Apply minimal change:
   - Only the keys necessary.
   - Preserve formatting and comments.

5. Suggest validation steps:
   - Run specific commands/tests.
   - Deploy to a non-production environment if applicable.

6. Summarize:
   - Exactly what changed.
   - How to revert if needed.

---

## 7. Workflow: Create a new knowledge pack for a project

**Goal:** Bootstrap a project-local Cursor pack for a repo.

**Steps:**

1. Inspect:
   - Project purpose and main tech stack.
   - Any existing docs and scripts.

2. Create a `docs/` directory if it doesn’t exist.

3. Create a file named:
   - `docs/2025MMDD_K1_<project>_CursorPack_v1.md`

4. Populate the file with sections:
   - Project overview.
   - Tech stack specifics.
   - Safety rules for this repo.
   - Frequently used commands.
   - Preferred workflows (e.g., how to run tests, how to deploy).
   - TODOs / open design questions.

5. Save the file and inform the user:
   - Explain how agents should use it going forward.
   - Suggest adding Pointer text into `.cursorrules` for this repo.

---

## 8. Extending this file

When the user identifies a repeated pattern that warrants a workflow:

1. Name the pattern clearly.
2. Add a new section in this file.
3. Follow the structure:
   - Goal.
   - Steps.
   - Notes/variants.

You must treat new workflows added here as first-class playbooks once they exist.
