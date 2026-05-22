# bwbsf.org

Website source for the Bay Area chapter of Burners Without Borders, published via GitHub Pages.

This repository includes an `agents/` git submodule that provides a plan-governed agent workflow framework for operational policy and reusable playbooks.

## Agent Framework Integration

Canonical policy source from host root:

* `./agents/RULES.md`

Root instruction shims:

* `AGENTS.md`
* `GEMINI.md`
* `CODEX.md`
* `CLAUDE.md`
* `OPENCODE.md`

Host-managed framework working copies (runtime-active in this repo):

* `playbooks/`
* `references/`
* `templates/`
* `scripts/`

Host-owned runtime state directories:

* `plans/future/`, `plans/current/`, `plans/past/`
* `journal/`
* `kanban/`
* `downtime/reports/pending/`, `downtime/reports/reviewed/`

Plan index command from host root:

```powershell
python agents/scripts/regenerate_plan_indexes.py --repo-root .
```

Verification command:

```powershell
python agents/scripts/regenerate_plan_indexes.py --check --repo-root .
```

## Stack and Publishing Model

This repository uses a GitHub Pages-compatible Jekyll structure:

* Markdown pages for site content (`index.md`, `blog/index.md`)
* Jekyll blog posts in `_posts/`
* Shared templates in `_layouts/`
* Shared header/footer includes in `_includes/`
* Global dark-mode stylesheet in `assets/css/site.css`

Publishing is intended through **GitHub Pages** from the repository root (typically `main` branch -> `/ (root)`).

## DevOps Workflow (GitHub Pages)

### 1. Configure GitHub Pages (one-time)

In the GitHub repository settings:

1. Open **Settings -> Pages**
2. Set **Source** to `Deploy from a branch`
3. Select branch `main`
4. Select folder `/ (root)`
5. Save

GitHub Pages will build and publish the Jekyll site on pushes to the configured branch.

### 2. Local Preview (recommended)

Prerequisites:

* Ruby
* Bundler

Install dependencies and run a local server:

```powershell
bundle install
bundle exec jekyll serve
```

Then open the local URL shown in the terminal (usually `http://127.0.0.1:4000`).

If Ruby/Jekyll is not available, changes can still be reviewed statically, but Liquid/Jekyll rendering should be verified before publishing.

### 3. Publish Changes

1. Edit content/layouts/styles
2. Verify locally (or document why local Jekyll verification was skipped)
3. Commit changes with a task-scoped message
4. Push to `origin`
5. Confirm the GitHub Pages site updates successfully

## Content Workflow

### Homepage

* `index.md` is the homepage.
* It includes a recent-posts section that automatically lists entries from `_posts/`.

### Blog

* `blog/index.md` is the blog landing page.
* New posts go in `_posts/` using this filename format:

```text
YYYY-MM-DD-title.md
```

Example:

```text
_posts/2026-02-24-welcome.md
```

Each post should include Jekyll front matter such as:

* `title`
* `date`
* `layout` (usually `post`, or rely on defaults in `_config.yml`)
* optional `author`
* optional `excerpt`

## Shared Templates

Header and footer are centralized and included in all templates via the default layout:

* `_includes/header.html`
* `_includes/footer.html`
* `_layouts/default.html`

Additional page-level layouts:

* `_layouts/page.html`
* `_layouts/post.html`

## Project Organization

Current top-level structure (relevant to site development):

* `_config.yml` - Jekyll and GitHub Pages site configuration
* `_includes/` - shared template fragments (header/footer)
* `_layouts/` - page/post/default layouts
* `_posts/` - blog posts
* `.gitmodules` - git submodule configuration
* `AGENTS.md` - host shim pointing to canonical policy in `./agents/RULES.md`
* `CLAUDE.md` - host shim for Claude runtimes
* `CODEX.md` - host shim for Codex runtimes
* `GEMINI.md` - host shim for Gemini runtimes
* `OPENCODE.md` - host shim for OpenCode runtimes
* `agents/` - upstream framework submodule (canonical policy and upstream source artifacts)
* `assets/css/` - site styles
* `blog/` - blog landing page
* `docs/` - host copies of framework supplemental docs (assimilation and migration references)
* `downtime/` - downtime tasks and report folders for analysis-only framework maintenance
* `index.md` - homepage
* `journal/` - daily operational journal entries
* `kanban/` - task boards for current and future work
* `plans/` - active/future/past execution plans and generated indexes
* `playbooks/` - host-managed operational workflows (framework defaults plus site-specific workflows)
* `references/` - reusable guidance used across playbooks and prompts
* `scripts/` - host-managed utility scripts used by framework workflows
* `templates/` - reusable output templates for plans, reports, and proposals

## Notes

* This is currently a static site with no client-side JavaScript modules.
* If JavaScript or backend scripts are added later, include appropriate logging/debugging hooks per `./agents/RULES.md`.
