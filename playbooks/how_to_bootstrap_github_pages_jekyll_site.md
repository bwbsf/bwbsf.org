# Playbook: How to Bootstrap a GitHub Pages Jekyll Site

*Status: Draft*

## Objective
Create a GitHub Pages-compatible Jekyll site skeleton with shared layouts/includes, initial homepage/blog content, and synchronized documentation updates.

## Prerequisites
* A git repository initialized for the website.
* `README.md` and `AGENTS.md` available and readable.
* User approval for an explicit file-by-file plan before edits.

## Step-by-Step Instructions

1. **Gather Context and Existing Policy**
   * Read `AGENTS.md` and `README.md`.
   * Review `playbooks/` for an existing site bootstrap workflow before creating a new one.
   * If no exact playbook exists, create one first using `playbooks/how_to_create_a_new_playbook.md`.

2. **Plan and Request Approval (Required)**
   * Propose an atomic plan that lists all files to add/update:
     * Jekyll config
     * Layouts/includes
     * Stylesheets/assets
     * Homepage/blog content
     * Documentation/playbooks
   * Ask clarifying questions about:
     * Site engine choice (Jekyll/GitHub Pages compatibility)
     * Initial content placeholders vs production copy
     * Whether a sample blog post should be added
   * Request explicit approval before making edits.

3. **Create GitHub Pages / Jekyll Structure**
   * Add/update the core files:
     * `_config.yml`
     * `_layouts/*.html`
     * `_includes/*.html`
     * `assets/css/site.css`
     * `index.md`
     * `blog/index.md`
     * `_posts/YYYY-MM-DD-title.md` (sample post if approved)
   * Ensure shared header/footer are included through the default layout used by all templates.

4. **Implement Shared Template Behavior**
   * Use a single default layout that includes:
     * `<head>` metadata
     * Header include
     * Footer include
     * Main content slot
   * Add page and post layouts that inherit from the default layout.
   * Confirm blog listings on the homepage and blog page use `site.posts`.

5. **Update Documentation**
   * Update `README.md` with:
     * Publishing workflow (GitHub Pages)
     * Local preview workflow
     * Site structure and where content lives
     * Shared template/include locations
   * Update `AGENTS.md` if playbooks were added/renamed.

6. **Verify**
   * Perform a static structure review (required).
   * If local Jekyll tooling is available, run the smallest local preview command (for example `bundle exec jekyll build` or `bundle exec jekyll serve`) and wait for completion before responding.
   * Confirm the site contains:
     * Homepage
     * Blog index
     * Shared header/footer
     * At least one post (if approved)

7. **Git Hygiene**
   * Run `git status -sb`.
   * Review the relevant diff.
   * Suggest a clear, task-scoped commit message.
   * Commit after user approval (follow `playbooks/how_to_commit_and_push_changes.md`).

## Verification
* Jekyll file structure exists and is internally consistent.
* Homepage and `/blog/` page both render post listings via Jekyll loops.
* `README.md` documents devops/publishing and project organization.
* `AGENTS.md` playbook index includes the new bootstrap workflow(s).

## Lifecycle Compliance
Prompt -> Plan (based on a known playbook) -> Request approval -> Execute -> Plan/playbook update -> Docs update -> Verification.

If inside a git repo:
* Review `git status` and diffs
* Suggest a commit message
* Commit after completion
* First law of vibe coding: commit after every completed change
