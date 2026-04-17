# Changelog

## 0.0.6

- Fixed inline `!` comments: now the full comment text after `!` is highlighted, not just the `!` character itself

## 0.0.5

- Fixed `parameter-names` falsely matching identifiers before negative numbers (e.g. `fixed` before `-837.8`)
- Added `vessel` and `Pinned` to MoorDyn keywords; made MoorDyn keyword matching case-insensitive
- Fixed `table-headers` to recognize column names containing `/` and `.` (e.g. `BA/-zeta`)

## 0.0.4

- Added TurbSim to extension name, description, and keywords

## 0.0.3

- Improved highlighting for OpenFAST output (`.out`) files
- Added recognition of output file description/metadata header lines (e.g. `Description from the FAST input file: ...`)

## 0.0.2

- Added VTK parameter keywords: `WrVTK`, `VTK_type`, `VTK_fields`, `VTK_fps`
- Added distinct highlighting for quoted special values: `"default"`, `"unused"`, `"none"`, `"True"`, `"False"`
- Fixed `{...}` and `[...]` blocks inside trailing descriptions now highlighted correctly instead of being consumed as plain comment text

## 0.0.1

- Initial release
- Added VS Code language registration for OpenFAST-style input files
- Added TextMate grammar for OpenFAST and ROSCO input syntax
- Added language configuration for comments, brackets, and quotes
- Added marketplace icon and extension metadata
