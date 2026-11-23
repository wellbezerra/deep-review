# Core checklist

Applied to every reviewed file, on top of the rule `ocr` resolves. Each
item is a question; report only when the answer is a concrete failure.

## Correctness

- Does every branch the change adds return or throw what its callers
  expect? Is there an input (empty, zero, missing, duplicate, very large)
  that takes a branch nobody handled?
- Are errors caught where they can be acted on, and do they reach the user
  as a message rather than a stack trace? Is a caught error ever swallowed?
- Does any resource (file handle, database connection, child process,
  timer) stay open on the error path?
- Do async calls get awaited? Can two of them race on the same state?

## Contracts

- Did a public function, CLI flag, exit code, output format or file format
  change? Who still depends on the old one?
- Do messages that tell the user what to do give a command that actually
  works?

## Portability (Windows, macOS, Linux)

- Paths: built with `path.join`/`resolve`, not string concatenation with
  `/`? Compared case-sensitively where Windows is case-insensitive?
- Shell advice in messages or docs: does it work in PowerShell? In
  Windows PowerShell 5.1, `>` writes UTF-16 LE, which a UTF-8 reader
  cannot parse.
- File operations: can Windows refuse them (`EBUSY`, `EPERM` on an open
  or locked file, a long path, a reserved name)?
- Line endings: does code that splits or compares text survive `\r\n`?

## Text and data

- Is text normalised the same way where it is written and where it is
  compared? Do non-Latin scripts and combining marks survive?
- Are numbers parsed and limits enforced where the data enters, not later?

## Tests

- Does changed behaviour come with a test that would fail without the
  change?
- Does the test assert on a result a user would recognise, not on how the
  code reaches it?
