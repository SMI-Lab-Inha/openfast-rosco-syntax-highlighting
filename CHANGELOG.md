# Changelog

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
