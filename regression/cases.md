# Regression cases

Commits that introduced a bug later fixed. After every change to SKILL.md
or a checklist, run deep-review on each case in its repository and record
in CHANGELOG.md whether the expected finding appeared (hit) or not (miss).
Run by hand; do not automate yet.

Repository: `wellbezerra/second-brain` (local clone).

| ID | Target | Expected finding | Fixed by |
|---|---|---|---|
| R1 | `-c 7f584c9` | `src/run/search.ts`: the hint `brain eval --json > run.json` fails under Windows PowerShell 5.1, where `>` writes UTF-16 and the UTF-8 read cannot parse it. Medium, environment unverified. | not fixed yet |
| R2 | `-c 563a621` | `src/index-db.ts` `Index.destroy`: `rmSync` throws `EBUSY` on Windows while another connection holds the index, and the error surfaces as a stack trace. | `0111860` |
| R3 | `-c 563a621` | `src/indexer.ts`: a batch is sent only once it reaches the batch size, so one call can carry far more texts than the cap (two notes → 90 texts, one long note → thousands). | `237c863` |
| R4 | `-c d9141a7` | `src/search-query.ts`: stripping combining marks before FTS5 turns words such as नमस्ते into terms the index never holds. | `88e22b0` |

Add a case whenever deep-review misses a bug that was found later.
