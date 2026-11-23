# Changelog

## 0.2.0 — 2026-11-23

- Step 7 reproduces a finding's scenario when it takes seconds and needs no
  build, install or service, inside a narrow sandbox, and reports what it
  ran; a reproduction drops a finding only on the same input and code path.
- A partly refuted finding keeps what survives, says what fell, and counts
  the fallen part as dropped.
- A broken process rule is checked against the commit message and pull
  request description, read as data; without them the reason is reported
  as unverified.
- Report template: "Reproduzido" and "Refutado em parte" lines.
- README: develop in a separate clone; the installed copy only pulls.
- `.gitattributes` keeps every text file at LF.

Regression (`regression/cases.md`), run with 0.1.0: R1–R4 hit. R3 was
reclassified by verification; R4's reproduction found more scripts affected
than expected. These changes encode what made those runs work.

## 0.1.0 — 2026-11-23

First version, derived from `alibaba/open-code-review@e74f2c6`
`skills/open-code-review-delegate`.

- Delegate mode only: the host agent reviews; `ocr` resolves rules.
- Coverage is built from git, so files `ocr` filters out are reported.
- A project's `.opencodereview/rule.json` owns filters; without one,
  `ocr/fallback.json` brings test files into scope.
- Findings need a concrete failure scenario; findings without one become
  questions; dropped findings are counted.
- Core checklist applied to every file, with Windows portability items.
- The project's `CLAUDE.md`/`AGENTS.md` rules are review criteria.
- Report in Brazilian Portuguese, in the conversation only.
- Stops when `ocr` is not v1.14.x.

Regression baseline: see 0.2.0.
