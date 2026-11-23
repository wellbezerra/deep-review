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

The installed copy in `~/.claude/skills/deep-review` is read-only by
convention: Claude Code treats `~/.claude` as sensitive and blocks edits
there. Develop in a separate clone, such as `~/Documents/develop/deep-review`,
from a session opened in that folder:

1. Edit, record the change in `CHANGELOG.md`, bump `metadata.version` in
   `SKILL.md`, commit and push.
2. Update the installed copy: `git -C ~/.claude/skills/deep-review pull --ff-only`.
3. Run the cases in `regression/cases.md` and record the results.

## Licence

Apache 2.0. Derived from Alibaba's Open Code Review; see `NOTICE`.
