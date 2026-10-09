# CLAUDE.md — Operating Manual

You maintain a paper-reading knowledge graph. Follow this exactly.

## Layers & permissions
- `papers/*.md` — my raw notes. **READ-ONLY. Never edit.**
- `index.md` — catalog, one row per paper. You maintain it.
- `meta/edges.md` — **the graph. Single source of truth for all edges.** You maintain it.
- `topics/*.md` — synthesis pages. You maintain them.
- `meta/tags.md` — canonical tags, aliases, topic list. You maintain it.

## Conventions
- Paper id = note filename stem, e.g. `papers/2024-depth-pro.md` → `2024-depth-pro`.
- Edge line format: `A --type--> B : one-line reason` (ids only).
- Record each edge ONCE in `meta/edges.md`. Never write the reverse edge; reverse is implied.
- Tags in the index must be canonical. If my note uses an alias, map it via `meta/tags.md` (don't edit my note).

## Ingest (when I say "ingest")
1. Read `index.md` and `meta/tags.md`.
2. Find notes in `papers/` whose id is not in the index. Read only those.
3. Pick likely relatives from the index (by tags + one-liners); read only those notes.
4. Append justified edges to `meta/edges.md`.
5. Add the paper to each topic page matching its tags; update that page's Overview if the paper changes the picture.
6. Append the index row (tags canonical).
7. Register any new tag in `meta/tags.md`. Create a new topic page only when a tag reaches 3 papers.
8. Print a summary: rows added, edges added (with reasons), pages touched.

## Edge types (closed set)
`extends` · `uses-method-from` · `competes-with` · `benchmarks-against` · `contradicts` · `same-problem`

## Hard rules
- Both ends of every edge must be ids in `index.md`. Never invent a paper. If my note mentions an unread paper, list it in the summary under "mentioned, not in corpus" — no edge.
- No edge without a reason. If unsure, skip the edge and mention it in the summary.
- Touch only the new paper's index row, its edges, its topic pages, and `meta/tags.md`.
- Never restructure topics during ingest. Never commit — I review and commit.

## Compact (when I say "compact")
Propose first, then apply after I confirm: merge duplicate topics, split topics over ~15 papers, fold near-duplicate tags into aliases (rewrite index tags accordingly), drop edges whose endpoints no longer exist.
