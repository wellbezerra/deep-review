# Regression cases

Commits that introduced a bug later fixed. After every change to SKILL.md
or a checklist, run deep-review on each case in its repository and record
in CHANGELOG.md whether the expected finding appeared (hit) or not (miss).
Run by hand; do not automate yet.

Repository: `wellbezerra/second-brain` (local clone).

| ID | Target | Expected finding | Fixed by | Last result |
|---|---|---|---|---|
| R1 | `-c 7f584c9` | `src/run/search.ts`: the hint `brain eval --json > run.json` fails under Windows PowerShell 5.1, where `>` writes UTF-16 and the UTF-8 read cannot parse it. Medium, environment unverified. | not fixed yet | hit (0.1.0, upstream skill, manual) |
| R2 | `-c 563a621` | `src/index-db.ts` `Index.destroy`: `rmSync` throws `EBUSY` on Windows while another connection holds the index, and the error surfaces as a stack trace. | `0111860` | hit (0.1.0) |
| R3 | `-c 563a621` | `src/indexer.ts`: a batch is sent only once it reaches the batch size, so one call can carry far more texts than the cap (two notes → 90 texts, one long note → thousands). | `237c863` | hit (0.1.0): reclassified as contract + lost progress; OllamaEmbedder already caps HTTP requests at 32 |
| R4 | `-c d9141a7` | `src/search-query.ts`: stripping combining marks before FTS5 turns words such as नमस्ते into terms the index never holds. | `88e22b0` | hit (0.1.0): reproduced in in-memory SQLite; Korean, Japanese kana with dakuten and Greek fail too |

Cases R1–R4 were known to the reviewer before it ran them, so a hit shows
the workflow can find the bug, not that it finds it blind. A miss on a fresh
change is the stronger signal: add it here.

Add a case whenever deep-review misses a bug that was found later.
