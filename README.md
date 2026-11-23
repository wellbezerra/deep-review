# deep-review

A Claude Code skill for reviewing code changes with the agent's own model.
The `ocr` CLI resolves per-file rules; git defines what changed; every
finding must come with a concrete failure scenario.

## Install

```sh
npm install -g @alibaba-group/open-code-review@1.14.2
git clone https://github.com/wellbezerra/deep-review.git ~/.claude/skills/deep-review
```

Then ask Claude Code to "review my changes", "review this branch" or
"review commit abc123".

## Per-project profile

A repository can add `.opencodereview/rule.json` to set its own filters
and rules (see the OCR docs on review rules). When it does, its `include`
should list test files, or they are left out.

## Changing the skill

Edit it from a session opened in this repository, not from a project that
uses it. Edits take effect as soon as they are on disk, so commit each
change, record it in `CHANGELOG.md`, and run the cases in
`regression/cases.md`.

## Licence

Apache 2.0. Derived from Alibaba's Open Code Review; see `NOTICE`.
