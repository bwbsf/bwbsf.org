# Playbook: How to Verify and Publish a GitHub Pages Site

*Status: Draft*

## Objective
Verify a Jekyll site changeset and publish it through GitHub Pages using a safe, repeatable workflow with documentation and git hygiene checks.

## Prerequisites
* Site changes already implemented.
* GitHub repository connected to a remote (`origin`).
* GitHub Pages configured (or ready to be configured) for this repository.

## Step-by-Step Instructions

1. **Confirm Scope and Plan**
   * Read `AGENTS.md` and `README.md`.
   * Confirm the changes being published are complete, including documentation updates.
   * If workflow gaps are discovered, update/create a playbook first.

2. **Local Verification (Preferred)**
   * If Ruby/Bundler/Jekyll tooling is installed:
     * Run `bundle install` (first-time setup) if dependencies are missing.
     * Run `bundle exec jekyll build` or `bundle exec jekyll serve`.
     * Wait synchronously for completion and capture errors.
   * If tooling is unavailable:
     * Perform a static file review and report that local Jekyll verification was not run.

3. **Content and Template Verification Checklist**
   * Confirm homepage exists (`index.md`) and renders shared header/footer.
   * Confirm blog landing page exists (`blog/index.md`) and lists posts.
   * Confirm post pages in `_posts/` use the shared post layout.
   * Confirm stylesheet/assets referenced by layouts exist.
   * Confirm `_config.yml` excludes non-site operational docs if intended.

4. **GitHub Pages Publishing Configuration (If Needed)**
   * In repository settings, configure GitHub Pages to publish from the intended source (commonly `main` branch, repository root).
   * If a custom domain is used, ensure `CNAME` handling is documented and consistent.
   * If deployment workflow changes (Actions vs branch build), update `README.md`.

5. **Git Hygiene and Commit**
   * Follow `playbooks/how_to_commit_and_push_changes.md`:
     * `git status -sb`
     * Review diff
     * Summarize changes
     * Propose commit message
     * Request approval
     * Commit
     * Push

6. **Post-Publish Verification**
   * Verify the public Pages URL renders the updated homepage and blog index.
   * Check for missing assets, broken navigation, or Liquid rendering issues.
   * If a publish failure occurs, use `playbooks/debugging_changes_that_lead_to_errors.md`.

## Verification
* Site builds locally or a documented static review was completed.
* GitHub Pages source configuration is documented.
* Changes are committed and pushed after approval.
* Public site is reachable and reflects the latest content.

## Lifecycle Compliance
Prompt -> Plan (based on a known playbook) -> Request approval -> Execute -> Plan/playbook update -> Docs update -> Verification.

If inside a git repo:
* Review `git status` and diffs
* Suggest a commit message
* Commit after completion
* First law of vibe coding: commit after every completed change
