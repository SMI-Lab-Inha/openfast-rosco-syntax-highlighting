# OpenFAST, ROSCO & TurbSim Syntax Highlighting

[![VS Code Marketplace](https://img.shields.io/badge/VS%20Code-Marketplace-blue)](https://marketplace.visualstudio.com/items?itemName=SMI-Lab.openfast-rosco-syntax-highlighting)

Unofficial VS Code extension for OpenFAST, ROSCO, and TurbSim input and output files.

## Features

- Syntax highlighting for OpenFAST-style text input files such as `.fst`, `.dat`, `.in`, `.inp`, `.out`, `.ipt`, `.ech`, `.wnd`, `.sum`, and `.bmi`
- Support for common OpenFAST module files including AeroDyn, ElastoDyn, HydroDyn, InflowWind, MoorDyn, ServoDyn, SeaState, and related driver files
- Support for ROSCO-style `DISCON.in` controller files
- Support for TurbSim input files (`.inp`)
- Highlighting for:
  - section banners and `END` markers
  - booleans and special values like `default`, `unused`, and `none`
  - quoted strings and file paths
  - integers, decimals, and scientific notation
  - parameter names in the common `value  parameter  - description` layout
  - `!` comments and trailing inline descriptions

## Installation

**From the VS Code Marketplace (recommended):**

1. Open VS Code.
2. Go to the Extensions view (`Ctrl+Shift+X`).
3. Search for **OpenFAST ROSCO Syntax Highlighting**.
4. Click **Install**.

**From a `.vsix` file:**

1. Download the `.vsix` file from the [Releases](https://github.com/SMI-Lab-Inha/openfast-rosco-syntax-highlighting/releases) page.
2. Open VS Code and go to the Extensions view (`Ctrl+Shift+X`).
3. Click the `...` menu at the top right and select **Install from VSIX...**.
4. Select the downloaded file.

Once installed, any file with a supported extension (`.fst`, `.dat`, `.in`, `.inp`, etc.) will be highlighted automatically.

## Scope

The grammar is built from real OpenFAST, ROSCO, and TurbSim sample files, not from a generic INI or config grammar.

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

## Notes

- Because `.dat` and `.in` are generic extensions, this extension may also match non-OpenFAST files if enabled globally.
- ROSCO YAML files are intentionally not claimed by this extension because standard YAML support in VS Code is usually the better default.
