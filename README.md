# tree-sitter-logo

A [tree-sitter](https://tree-sitter.github.io/) grammar for Logo, as [UCBLogo](https://people.eecs.berkeley.edu/~bh/logo.html) and [Pendown](https://github.com/dflock/pendown) speak it. The [Zed](https://zed.dev/) extension that uses it is [zed-logo](https://github.com/dflock/zed-logo).

## What it parses

Tree-sitter can't know how many inputs a procedure takes, so it can't group an instruction with its inputs as Logo's own parser does. It parses the tokens and the structure:

- words, numbers, `"quoted` words, `:variables` and the infix operators;
- `[...]` lists, `{...}` arrays (with `@origin`), `(...)` and `;` comments;
- `TO ... END` definitions, on several lines or one, in any case: the name, the inputs, and the body.

That's enough for colours, brackets, outlines, indentation and folding. UCBLogo's optional inputs on a title line, `[:size 100]`, parse as a list starting the body.

## Queries

- `highlights.scm`: Pendown's built-in commands and special variables are listed in it, generated from `content/reference.kdl` in Pendown's repository. zed-logo has its own copy of all these queries.
- `brackets.scm`, `outline.scm` (procedures), `indents.scm` and `folds.scm`.

No two highlight patterns match the same node, since editors differ about which pattern wins.

## Working on it

With Node:

```sh
npx tree-sitter-cli@0.25.10 generate
npx tree-sitter-cli@0.25.10 test
```

`test/corpus/` has the parse tests, and `test/highlight/` the highlight tests.

## Licence

GPLv3: see `LICENSE`.
