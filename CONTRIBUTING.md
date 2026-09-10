# Contributing to XPUI

Ten repositories, one standard. **Each carries its own `docs/contributing.md`**
with what is true only there: how to build it, which gate stages it runs, which
style rules bite. Read that one first — this page is only what holds
everywhere.

[`docs/orientation.md`](https://github.com/XPUI-Framework/xpui-framework/blob/main/docs/orientation.md)
is where the ten repositories, how they sit on disk, and the traps that have
already cost a day are explained.

## The gate

A change is not finished until `./build-and-test.sh` passes. Every repository
has one, and it is the script its CI runs. The modes differ, and the repository's
own guide is what lists them: in nine of the ten the bare command is exactly what
CI checks, and `fix` formats in place first. The umbrella is the exception — CI
runs `cross`, the cross-repository half, while the bare command adds every
sibling's gate on top of it.

## The review

Five steps, in order, none skipped:

1. The gate passes, with the real exit code read.
2. The code-reviewer agent reviews the change — every finding resolved, not
   noted.
3. The docs-reviewer agent reviews the prose, last: it runs every command a
   document gives and resolves every snippet against the API.
4. The author reviews the code and runs it — in the simulator, on a board, or
   through the C++ host, whichever the change reaches. That step is theirs; a
   running screen is not an agent's to sign off.
5. They say commit.

A test that cannot fail is worse than no test. Before adding one, break the
code on purpose and confirm the test notices. Prefer an assertion that pins a
relationship over one that pins a number.

## Commits

The subject says what was done — imperative, under fifty characters, one
concern. The body says what changed and why, in under about ten lines,
carrying the fact that is not in the diff. Nothing about how the bug was
found. No self-attribution.
