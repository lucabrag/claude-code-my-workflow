# Plan: Create Clean clo-author Template Repository

**Status:** DRAFT
**Date:** 2026-04-08

## Context

Luca built a paper-focused research workflow in `MeaningfulInformationClaude/` with significant improvements over the original `hugosantanna/clo-author`: consolidated 10-skill architecture, 18 research-pipeline agents, journal profiles, simulated peer review, R&R cycle, etc. This plan creates a **clean, reusable template** at `~/Documents/GitHub/clo-author-template/` that captures all architectural improvements while stripping project-specific content.

## Approach

Create a new git repo with the full infrastructure, replacing all MeaningfulInformation-specific content with `[PLACEHOLDER]` patterns matching the style already used in `claude-code-my-workflow`'s CLAUDE.md.

## Files to Create

### Keep as-is (generic, no changes needed)
These files are already generic — copy verbatim:

| Source | Destination |
|--------|-------------|
| `.claude/agents/orchestrator.md` | same |
| `.claude/agents/editor.md` | same |
| `.claude/agents/domain-referee.md` | same |
| `.claude/agents/methods-referee.md` | same |
| `.claude/agents/librarian.md` | same |
| `.claude/agents/librarian-critic.md` | same |
| `.claude/agents/explorer.md` | same |
| `.claude/agents/explorer-critic.md` | same |
| `.claude/agents/data-engineer.md` | same |
| `.claude/agents/strategist.md` | same |
| `.claude/agents/strategist-critic.md` | same |
| `.claude/agents/coder.md` | same |
| `.claude/agents/coder-critic.md` | same |
| `.claude/agents/writer.md` | same |
| `.claude/agents/writer-critic.md` | same |
| `.claude/agents/storyteller.md` | same |
| `.claude/agents/storyteller-critic.md` | same |
| `.claude/agents/verifier.md` | same |
| `.claude/skills/*` (all 10) | same |
| `.claude/rules/agents.md` | same |
| `.claude/rules/workflow.md` | same |
| `.claude/rules/quality.md` | same |
| `.claude/rules/revision.md` | same |
| `.claude/rules/content-standards.md` | same |
| `.claude/rules/logging.md` | same |
| `.claude/rules/working-paper-format.md` | same |
| `.claude/references/journal-profiles.md` | same |
| `.claude/hooks/protect-files.sh` | same |
| `.claude/hooks/pre-compact.py` | same |
| `.claude/hooks/post-compact-restore.py` | same |
| `.claude/hooks/post-merge.sh` | same |
| `.claude/WORKFLOW_QUICK_REF.md` | same |
| `templates/*` (all 7) | same |

### Templatize (replace project-specific content with placeholders)

1. **`CLAUDE.md`** — Replace project name, institution, field, folder structure, compilation commands, current state table with `[YOUR ...]` placeholders. Keep the structure and all skill references.

2. **`.claude/references/domain-profile.md`** — Replace Microeconomic Theory / Information Economics content with placeholder structure. Keep the table headers and format, replace the rows with `[YOUR ...]` examples from multiple domains.

3. **`.claude/settings.json`** — Keep all generic permissions (git, gh, LaTeX, R, Python). Keep hooks. Remove Stata-specific permissions (add as commented example).

4. **`.claude/rules/meta-governance.md`** — Keep generic version (already mostly generic).

5. **`MEMORY.md`** — Keep the generic [LEARN] entries about workflow patterns, documentation standards, design philosophy. Strip any project-specific entries.

### Create new (template scaffolding)

1. **`README.md`** — Template README explaining what's included, how to use, quick start guide
2. **Empty directory structure:**
   - `paper/` with `main.tex` (minimal placeholder), `sections/`, `figures/`, `tables/`, `talks/`, `preambles/`, `supplementary/`, `replication/`
   - `data/raw/`, `data/cleaned/`
   - `scripts/R/`, `scripts/stata/`, `scripts/python/`
   - `quality_reports/plans/`, `quality_reports/session_logs/`, `quality_reports/reviews/`, `quality_reports/merges/`, `quality_reports/specs/`
   - `explorations/`
   - `master_supporting_docs/`
3. **`.gitignore`** — Comprehensive academic project gitignore (LaTeX aux, data, IDE, OS files)
4. **`Bibliography_base.bib`** — Empty placeholder with comment header

### Strip entirely (do NOT copy)
- `paper/main.tex` and all content files
- `paper/figures/*`, `paper/tables/*`
- `data/raw/*`, `data/cleaned/*`
- `scripts/stata/*.do`, `scripts/python/fig_theorem5_simplex.py`
- `quality_reports/reviews/*` (project-specific review outputs)
- `scripts/sync_to_docs.sh` (broken, from wrong template)
- `.claude/state/` (session state, gitignored anyway)

## Execution Order

1. Create directory + `git init`
2. Copy all as-is files (agents, skills, rules, hooks, references, templates, WORKFLOW_QUICK_REF)
3. Create templatized files (CLAUDE.md, domain-profile.md, settings.json, meta-governance.md, MEMORY.md)
4. Create scaffolding (README, directory structure with .gitkeep, .gitignore, Bibliography_base.bib)
5. `git add -A && git commit`

## Verification

- [ ] All 18 agents present and readable
- [ ] All 10 skills present and executable
- [ ] All 8 rules present
- [ ] journal-profiles.md present with all 30+ profiles
- [ ] domain-profile.md has placeholder structure
- [ ] CLAUDE.md has all placeholder markers
- [ ] settings.json has valid JSON
- [ ] hooks are executable (chmod +x)
- [ ] Directory structure complete with .gitkeep files
- [ ] No project-specific content leaked (grep for "Meaningful Information", "Braghieri", "Chile", "AL2018", etc.)
- [ ] Git repo initialized with clean first commit

## Estimated Scope

~50 files to copy, ~5 files to templatize, ~5 files to create new. One commit.
