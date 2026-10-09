# Paper Garden

A git-backed, LLM-maintained reading graph. You write one note per paper; the agent maintains the index, the edge list, and topic pages.

## Setup (once)
`git init && git add -A && git commit -m "scaffold"`

## Daily loop
1. `cp templates/paper-note.md papers/YYYY-shortname.md` (YYYY = publication year; filename = paper id)
2. Fill in your 90-second take. Touch nothing else.
3. In Claude Code, in this repo: **"ingest"**
4. `git diff` — check every new edge in `meta/edges.md` is real.
5. `git add -A && git commit -m "read: shortname"`

Commit history = your reading timeline.

## Every week or two
In Claude Code: **"compact"**. Review its proposal, confirm, commit separately.

## Layout
- `papers/` — your notes (agent never edits)
- `index.md` — catalog, the agent's working memory
- `meta/edges.md` — the graph (typed edges)
- `topics/` — synthesis pages
- `meta/tags.md` — canonical tags + aliases + topic list
- `CLAUDE.md` — the agent's contract
