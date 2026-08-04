# NLP++ TextMate Grammars

TextMate grammars for **NLP++**, the programming language built for natural language
processing, and for the supporting VisualText file formats.

These are the canonical, license-clean source grammars. They are extracted from the
[VS Code NLP++ extension](https://github.com/VisualText/vscode-nlp) so that downstream
projects — GitHub Linguist, Shiki, `bat`, Sublime Text, JetBrains IDEs, and anything else
that consumes TextMate grammars — can vendor them directly without pulling in the whole
extension.

## Grammars

| File | Scope name | Extensions | Description |
|---|---|---|---|
| `syntaxes/nlp.tmLanguage.json` | `source.nlp` | `.nlp`, `.pat` | **NLP++ language** — rules, regions, and code |
| `syntaxes/dict.tmLanguage.json` | `source.dict` | `.dict` | Dictionary files |
| `syntaxes/kb.tmLanguage.json` | `source.kb` | `.kb` | Knowledge base dumps |
| `syntaxes/kbb.tmLanguage.json` | `source.kbb` | `.kbb` | Knowledge base build files |
| `syntaxes/tree.tmLanguage.json` | `source.tree` | `.tree`, `.log` | Parse tree output |
| `syntaxes/txxt.tmLanguage.json` | `source.txxt` | `.txxt` | Highlighted text output |
| `syntaxes/seq.tmLanguage.json` | `source.seq` | `.seq` | Analyzer pass sequence files |

`source.nlp` is the one most integrations want. The others describe VisualText's data and
output formats rather than the language itself.

Matching VS Code language configurations (brackets, comments, auto-closing pairs) are in
[`language-configuration/`](language-configuration/).

## Comments

`#` runs to end of line. C-style `/* ... */` block comments are supported by the NLP++
engine as of version 3.7.14, in the pass language (`.nlp`, `.pat`) and in the four
line-oriented data formats (`.seq`, `.kb`, `.dict`, `.kbb`). They do not nest — the first
`*/` closes — and delimiters inside a string or a `#` comment are ordinary text. `.tree`
files are engine output and use `*` line comments only.

## Samples

[`samples/`](samples/) contains real-world NLP++ from the
[parse-en-us](https://github.com/VisualText/parse-en-us) English parser (MIT licensed,
same authors) — useful for grammar regression testing and for submissions that require
non-trivial example code.

## Using these grammars

**Shiki / VS Code / any TextMate host** — point at the raw JSON:

```js
const nlp = await fetch(
  'https://raw.githubusercontent.com/VisualText/nlpplus-tmbundle/main/syntaxes/nlp.tmLanguage.json'
).then(r => r.json())
```

**Vendoring** — add this repository as a git submodule. It is intentionally small and has
no build step, no dependencies, and no generated files.

## About NLP++

NLP++ is a programming language designed specifically for natural language processing,
created by Amnon Meyers and David de Hilster. Analyzers are written as sequences of passes,
each applying pattern rules to a parse tree. See [visualtext.org](https://visualtext.org).

## License

MIT — see [LICENSE](LICENSE). Copyright 1998- Amnon Meyers, David de Hilster.
