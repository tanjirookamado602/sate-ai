# Changelog

All notable changes to SATE AI are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/)
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- New `sate_cli` package — installable with `dart pub global activate sate_cli`
  without requiring Flutter (Issue #119)
- New `CLI` GitHub Actions workflow that runs on `dart:stable` to prove the
  CLI works with no Flutter SDK installed

### Changed
- CLI entry point moved from `bin/sate_ai.dart` to `packages/sate_cli/bin/sate_ai.dart`
- `lib/sate_ai_cli.dart` in the Flutter package now re-exports `sate_core`
  and is marked deprecated (kept for backwards compatibility)
- Refactored architecture to extract pure Dart core into `sate_core` package (Issue #118)
  - Created standalone `packages/sate_core` package with no Flutter dependency
  - Moved core types, injectors, analyzers, i18n, and mock adapters into `sate_core`
  - Re-exported `sate_core` from root `sate_ai` and `sate_ai_cli` barrels
  - Preserved Flutter-native adapters (`OnnxAdapter`, `TFLiteAdapter`, `FllamaAdapter`) in `sate_ai`

### Added
- SQLite storage for historical reports (Issue #92)
  - `ReportDatabase` class backed by `sqflite_common_ffi`
  - CRUD: insert, queryRecent, queryByModel, queryByDateRange, count, delete
  - CLI flags `--db <path>` and `--db-history`
- CI/CD status badges generator (Issue #91)
  - `BadgeGenerator` for SVG badges (status, tests, inference, memory)
  - CLI flag `--badge-output`
- Custom report templates (Issue #90)
  - `TemplateEngine` and `TemplateLoader` for JSON/YAML templates
  - CLI flag `--template`
- Model health check API (Issue #89)
  - `SateAI.healthCheck(model)` and `HealthCheckResult`
  - CLI flag `--health-check`
- Auto-detect model type in batch mode (Issue #88)
  - `ModelTypeDetector` and `ModelFactory`
  - CLI flag `--auto-detect`

## [0.12.0] - 2026-09-15

### Added
- Report comparison and diff view (Issue #74)
- Performance benchmarking mode (Issue #75)
- Stress test retry and flaky test detection (Issue #73)
- VS Code extension (Issue #37)

## [0.11.0] - 2026-09-05

### Added
- CLI code generation for custom injectors (Issue #39)
- Stress test scheduling via cron (Issue #34)
- Golden baseline comparisons (Issue #35)
- Batch mode for multiple models (Issue #36)

## [0.10.0] - 2026-09-01

### Added
- Real-time monitoring dashboard (Issue #33)
- HTML report export with Chart.js (Issue #32)
- MediaPipe adapter (Issue #29)
- Core ML adapter (Issue #30)
- Google ML Kit adapter (Issue #31)

## [0.9.0] - 2026-08-21

### Added
- TensorFlow Lite adapter (Issue #4)
- Confidence threshold injector (Issue #6)
- Data corruption injector (Issue #26)
- Model version mismatch injector (Issue #27)
- Network latency/drop injector (Issue #25)

## [0.8.0] - 2026-08-12

### Added
- Fllama (llama.cpp) adapter (Issue #28)

## [0.7.0] - 2026-08-05

### Added
- Latency injector
- Model swap injector
- Interactive demo on website

## [0.6.0] - 2026-07-30

### Added
- Thermal throttle injector (Issue #5)

## [0.5.0] - 2026-07-29

### Added
- CLI executable `sate_ai`
- GitHub composite action

## [0.4.0] - 2026-07-28

### Added
- Quantization drift injector (Issue #2)

## [0.3.0] - 2026-07-28

### Added
- Web dashboard with dark mode and exports

## [0.2.0] - 2026-07-28

### Added
- ONNX Runtime adapter (Issue #1)

## [0.1.0] - 2026-07-28

### Added
- Initial release: core framework, MockAdapter, MemoryPressureInjector, MalformedInputInjector
- 59 unit tests

[Unreleased]: https://github.com/assassinaj602/sate_ai/compare/v0.13.0...HEAD
[0.13.0]: https://github.com/assassinaj602/sate_ai/compare/v0.12.0...v0.13.0
[0.12.0]: https://github.com/assassinaj602/sate_ai/compare/v0.11.0...v0.12.0
[0.11.0]: https://github.com/assassinaj602/sate_ai/compare/v0.10.0...v0.11.0
[0.10.0]: https://github.com/assassinaj602/sate_ai/compare/v0.9.0...v0.10.0
[0.9.0]: https://github.com/assassinaj602/sate_ai/compare/v0.8.0...v0.9.0
[0.8.0]: https://github.com/assassinaj602/sate_ai/compare/v0.7.0...v0.8.0
[0.7.0]: https://github.com/assassinaj602/sate_ai/compare/v0.6.0...v0.7.0
[0.6.0]: https://github.com/assassinaj602/sate_ai/compare/v0.5.0...v0.6.0
[0.5.0]: https://github.com/assassinaj602/sate_ai/compare/v0.4.0...v0.5.0
[0.4.0]: https://github.com/assassinaj602/sate_ai/compare/v0.3.0...v0.4.0
[0.3.0]: https://github.com/assassinaj602/sate_ai/compare/v0.2.0...v0.3.0
[0.2.0]: https://github.com/assassinaj602/sate_ai/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/assassinaj602/sate_ai/releases/tag/v0.1.0
