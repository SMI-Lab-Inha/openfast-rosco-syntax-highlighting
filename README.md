# OpenFAST & ROSCO Syntax Highlighting

Unofficial VS Code extension for OpenFAST input files and ROSCO controller input files.

## Features

- Syntax highlighting for OpenFAST-style text input files such as `.fst`, `.dat`, `.in`, `.inp`, `.out`, `.ipt`, `.ech`, `.wnd`, `.sum`, and `.bmi`
- Support for common OpenFAST module files including AeroDyn, ElastoDyn, HydroDyn, InflowWind, MoorDyn, ServoDyn, SeaState, and related driver files
- Support for ROSCO-style `DISCON.in` controller files
- Highlighting for:
  - section banners and `END` markers
  - booleans and special values like `default`, `unused`, and `none`
  - quoted strings and file paths
  - integers, decimals, and scientific notation
  - parameter names in the common `value  parameter  - description` layout
  - `!` comments and trailing inline descriptions

## Scope

The grammar is built from real OpenFAST and ROSCO sample files in this repository, not from a generic INI or config grammar.

It is designed to make engineering input decks easier to read without trying to fully parse every module format.

## Included Files

- `syntaxes/openfast.tmLanguage.json`
- `language-configuration.json`
- `media/icon.png`

## Development

1. Open this folder in Visual Studio Code.
2. Run `Extensions: Show Running Extensions`.
3. Press `F5` to launch an Extension Development Host.
4. Open an OpenFAST or ROSCO input file in the new window and verify highlighting.

## Packaging

To package for sharing or publication:

1. Install `vsce`
2. Run `vsce package`

This repository includes a `.vscodeignore` file so the sample turbine data is not bundled into the published extension.

## Notes

- The initial migration reference was `openfast_udl.xml`, but the grammar behavior is guided by the real sample files.
- Because `.dat` and `.in` are generic extensions, this extension may also match non-OpenFAST files if enabled globally.
- ROSCO YAML files are intentionally not claimed by this extension because standard YAML support in VS Code is usually the better default.
