# Playbook: How to Import Agents Submodule and Plan Framework Migration

*Status: Draft*

## Objective
Provide a repeatable workflow to import an external agents-framework repository as a submodule and produce an approval-ready migration plan for replacing local governance docs (`AGENTS.md`, playbooks, and related documentation).

## Prerequisites
* Existing repository with `AGENTS.md` and `playbooks/`.
* A user-approved intent to evaluate or adopt an external framework.
* Git access to the target framework repository URL.

## Step-by-Step Instructions

1. **Read Local Operating Context**
   * Read `AGENTS.md`, `./agents/RULES.md` (after submodule import), `README.md`, and relevant existing playbooks.
   * Confirm documentation integrity requirements and commit workflow expectations.

2. **Prepare a Plan and Request Approval**
   * List all files expected to change before modifying anything.
   * Identify missing inputs (target repo URL, target submodule path, migration scope).
   * Request explicit user approval to proceed.

3. **Import Framework as a Submodule**
   * Add the framework as a submodule at the approved path (for example `./agents`).
   * If network or sandbox restrictions block fetch operations, request escalation and retry.
   * Verify the submodule is initialized and has a checked-out commit.

4. **Inspect Framework Instructions**
   * Read the framework's primary policy and process files (for example `AGENTS.md`, playbooks, templates, or docs).
   * Capture required conventions, mandatory files, and expected workflows.

5. **Produce a Migration Mapping**
   * Map each current local governance artifact to its proposed target in the new framework:
     * `AGENTS.md`
     * `playbooks/*.md`
     * Any process references in `README.md` and related docs
   * Mark each item as: keep, replace, merge, or deprecate.

6. **Draft an Atomic Migration Plan**
   * Create an execution plan with ordered steps, file-level edits, and risk notes.
   * Include rollback strategy and verification points.
   * Present this plan to the user and request approval before applying framework-replacement edits.

7. **Update Local Docs for Structural Changes**
   * If a new top-level directory is added (for example `agents/`), update `README.md` project organization.
   * Update host shim files only if canonical policy path or shim behavior changes.

8. **Verification and Git Hygiene**
   * Run `git status -sb`.
   * Review relevant diffs for intended-only changes.
   * Suggest a commit message summarizing completed work.
   * Commit after approval.

## Verification
* Submodule exists at the approved path and points to a specific commit.
* Framework instructions are inspected and summarized.
* Migration plan is concrete, file-specific, and approval-ready.
* Documentation reflects any structural repo changes.

## Lifecycle Compliance
Prompt -> Select/Create Plan (using relevant playbook guidance) -> Request approval -> Execute approved plan atoms -> Plan update -> Docs update -> Verification.

If inside a git repo:
* Review `git status` and relevant diffs.
* Suggest a commit message that summarizes the completed task.
* Commit after approved checkpoint completion.
