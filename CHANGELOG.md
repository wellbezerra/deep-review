# Changelog

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

Regression baseline (`regression/cases.md`):
R1 hit (found manually with the upstream skill before this version);
R2, R3, R4 not yet run.
