# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A VS Code extension that provides syntax highlighting for OpenFAST input files and ROSCO controller files. Published as `openfast-rosco-syntax-highlighting` by `SMI-Lab`.

## Development Workflow

**Run/test the extension:**

1. Open this folder in VS Code.
2. Press `F5` to launch an Extension Development Host.
3. Open any `.fst`, `.dat`, or `.in` file and verify highlighting.

**Package the extension:**

```bash
vsce package
```

Requires `vsce` installed globally (`npm install -g @vscode/vsce`). The `.vscodeignore` excludes sample turbine data from the bundle.

## Key Files

- [syntaxes/openfast.tmLanguage.json](syntaxes/openfast.tmLanguage.json) — the TextMate grammar; all highlighting logic lives here
- [package.json](package.json) — extension manifest; defines file extension associations (`.fst`, `.dat`, `.in`, `.inp`, `.out`, `.ipt`, `.ech`, `.wnd`, `.sum`, `.bmi`) and links to the grammar
- [language-configuration.json](language-configuration.json) — comment character (`!`), bracket pairs, auto-closing pairs
- `openfast_udl.xml` — original Notepad++ UDL reference kept locally only (not in repo); grammar decisions should be driven by real sample files

## Grammar Architecture

The grammar (`source.openfast`) applies patterns in priority order:

1. **`file-opening`** — first 1–2 lines as headings (`markup.heading`)
2. **`full-line-comments`** — lines starting with `!` (`comment.line.bang`)
3. **`section-banners`** — lines of repeated `-` or `=` (`markup.heading`)
4. **`end-marker`** — `END` at line start (`keyword.control.end`)
5. **`quoted-special-values`** — `"default"`, `"none"`, etc. before general strings
6. **`strings`** — double-quoted strings; path strings detected by heuristic (drive letter, slashes, file extension)
7. **`special-values`** — bare `True`/`False`, `default`, `unused`, `none`
8. **`moordyn-keywords`** — `Free`, `Fixed`, `Coupled`
9. **`vtk-keywords`** — VTK output parameter names
10. **`numbers`** — integers, decimals, scientific notation (including `D`/`d` Fortran exponent)
11. **`parameter-names`** — identifiers followed by `-` or `!`, including indexed forms like `BDBldFile(1)`
12. **`table-headers`** — all-identifier lines (no values, no `!`, no `---`)
13. **`units-rows`** — lines of parenthesised unit tokens like `(m)  (deg)  (s)`
14. **`trailing-descriptions`** — text after ` - ` treated as a comment; contains nested `available-options` and `typed-annotations`
15. **`typed-annotations`** — `(flag)`, `(switch)`, `(string)` etc.
16. **`available-options`** — `{...}` and `[...]` blocks listing enumerated choices
17. **`bang-comments`** — inline `!` markers
18. **`punctuation`** — bare `{}`, `[]`, `()`

## Sample Files (Acceptance Corpus)

The IEA-15-240-RWT turbine files are kept locally (excluded from the repo via `.gitignore`) and used to validate grammar behavior. Representative files to test against:

- `IEA-15-240-RWT-UMaineSemi/Main_6_1.fst` — top-level `.fst` driver
- `IEA-15-240-RWT-UMaineSemi/IEA-15-240-RWT-UMaineSemi_AeroDyn.dat` — AeroDyn module
- `IEA-15-240-RWT-UMaineSemi/IEA-15-240-RWT-UMaineSemi_DISCON.in` — ROSCO controller (`!` comments)
- `IEA-15-240-RWT/IEA-15-240-RWT-ElastoDyn_tower.dat` — ElastoDyn tower file

## Important Syntax Notes

- Most lines follow: `value    ParameterName    - description`
- `!` is the comment character for ROSCO/DISCON-style files; `-` introduces inline descriptions in OpenFAST-style files
- Section banners are lines of repeated `---` or `===`; the `END` keyword closes input sections
- Fortran double-precision scientific notation uses `D`/`d` as exponent separator (e.g., `1.464D-05`)
- Parameter names may include array indexing: `BDBldFile(1)`, `WaveKinGridxi(1,1)`
- ROSCO YAML files are intentionally not claimed by this extension (VS Code's built-in YAML handles them)
