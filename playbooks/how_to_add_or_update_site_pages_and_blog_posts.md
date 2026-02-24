# Playbook: How to Add or Update Site Pages and Blog Posts

*Status: Draft*

## Objective
Provide a repeatable workflow for editing site pages and blog posts in the Jekyll/GitHub Pages site while preserving shared template behavior and documentation integrity.

## Prerequisites
* Existing Jekyll site structure with `_layouts/`, `_includes/`, and `_posts/`.
* User-approved plan for the requested content/design changes.
* Awareness of any existing style/content conventions in `README.md`.

## Step-by-Step Instructions

1. **Read Relevant Context**
   * Read `AGENTS.md` and `README.md`.
   * Identify whether the task is:
     * A content-only page/post update
     * A layout/include change affecting multiple pages
     * A structural change (new directories/pages)

2. **Plan and Request Approval (Required)**
   * List every file to modify.
   * Call out documentation updates (`README.md`, `AGENTS.md`, playbooks) if structure/workflows change.
   * Ask clarifying questions if copy, navigation, or URL structure is ambiguous.
   * Request approval before editing.

3. **Edit Pages or Posts**
   * For pages:
     * Use front matter with an appropriate layout (for example `layout: page` or `layout: default`).
     * Keep reusable header/footer behavior in layouts/includes, not duplicated in page files.
   * For posts:
     * Create files in `_posts/` using `YYYY-MM-DD-title.md`.
     * Include front matter (`title`, `date`, and optional `author`, `excerpt`).
   * Preserve GitHub Pages/Jekyll compatibility (Liquid/Markdown syntax supported by Jekyll).

4. **Handle Shared Templates Carefully**
   * If changing `_layouts/` or `_includes/`, verify the impact on:
     * Homepage (`index.md`)
     * Blog index (`blog/index.md`)
     * Post pages (`_posts/*`)
   * Keep header and footer centralized in includes.

5. **Update Documentation (When Needed)**
   * Update `README.md` immediately if:
     * Site structure changes
     * Publishing/local preview workflow changes
     * New directories/files become part of the standard workflow
   * Update `AGENTS.md` if playbook inventory changes.
   * Update playbooks if the workflow itself changes.

6. **Verify**
   * Static review of edited pages/posts and shared layouts.
   * If tooling is available, run a local Jekyll preview/build and wait for completion.
   * Confirm expected navigation links and post listings still work.

7. **Git Hygiene**
   * Run `git status -sb`.
   * Review diff for unintended layout-wide regressions.
   * Suggest a commit message and commit after approval.

## Verification
* Requested page/post content changes are present.
* Shared header/footer continue to render through templates.
* Homepage/blog listing remains valid if posts were added/edited.
* Docs are updated if structure/workflow changed.

## Lifecycle Compliance
Prompt -> Plan (based on a known playbook) -> Request approval -> Execute -> Plan/playbook update -> Docs update -> Verification.

If inside a git repo:
* Review `git status` and diffs
* Suggest a commit message
* Commit after completion
* First law of vibe coding: commit after every completed change
