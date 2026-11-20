# Changelog

All notable changes to SATE AI are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/)
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- New `sate_cli` package - installable with `dart pub global activate sate_cli`
  without requiring Flutter (Issue #119)
- New `CLI` GitHub Actions workflow that runs on `dart:stable` to prove the
  CLI works with no Flutter SDK installed

### Changed
- Refactored architecture to extract pure Dart core into `sate_core` package (Issue #118)
  - Created standalone `packages/sate_core` package with no Flutter dependency
  - Moved core types, injectors, analyzers, i18n, and mock adapters into `sate_core`
  - Re-exported `sate_core` from root `sate_ai` and `sate_ai_cli` barrels
  - Preserved Flutter-native adapters (`OnnxAdapter`, `TFLiteAdapter`, `FllamaAdapter`) in `sate_ai`

### Added
- Webhook notifications for stress test results (Issue #94)
  - `WebhookNotifier` supporting Slack, Discord, and Microsoft Teams
  - `WebhookPayload` builders for each provider
  - CLI flags `--webhook-url`, `--webhook-type`, `--webhook-on-pass`
  - 10+ unit tests
- Detailed model performance profiling (Issue #93)
  - `ProfileResult` with per-stage timing and memory
  - `InferenceProfiler` for staged profiling
  - CLI flags `--profile` and `--profile-runs`
  - 10+ unit tests

## [0.11.0] - 2026-09-26

### Added
- SQLite storage for historical reports (Issue #92)
  - `ReportDatabase` class for local report persistence using `sqflite_common_ffi`
  - CRUD operations (`insertReport`, `queryRecent`, `queryByModel`, `queryByDateRange`, `count`, `deleteByModel`, `deleteAll`)
  - CLI `--db` and `--db-history` options to automatically save and query historical stress reports
  - Unit tests covering DB initialization, query filters, data integrity, and error handling

### Changed
- Documentation and CLI usage updated with SQLite database storage options

## [0.13.0] - 2026-09-24

### Added
- CI/CD Status Badges (Issue #91)
  - `BadgeGenerator` for generating SVG status badges (shields.io format)
  - `BadgeType` enum supporting `status`, `latency`, `memory`, and `tests` badges
  - `StressReport.toBadge()` and `writeBadgeToFile()` helpers
  - CLI flags `--badge` and `--badge-type`
  - 12+ unit tests

### Changed
- Documentation updated with CI/CD status badges usage

## [0.12.0] - 2026-09-22

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

[Unreleased]: https://github.com/tanjirookamado602/sate-ai/compare/v0.13.0...HEAD
[0.13.0]: https://github.com/tanjirookamado602/sate-ai/compare/v0.12.0...v0.13.0
[0.12.0]: https://github.com/tanjirookamado602/sate-ai/compare/v0.11.0...v0.12.0
[0.11.0]: https://github.com/tanjirookamado602/sate-ai/compare/v0.10.0...v0.11.0
[0.10.0]: https://github.com/tanjirookamado602/sate-ai/compare/v0.9.0...v0.10.0
[0.9.0]: https://github.com/tanjirookamado602/sate-ai/compare/v0.8.0...v0.9.0
[0.8.0]: https://github.com/tanjirookamado602/sate-ai/compare/v0.7.0...v0.8.0
[0.7.0]: https://github.com/tanjirookamado602/sate-ai/compare/v0.6.0...v0.7.0
[0.6.0]: https://github.com/tanjirookamado602/sate-ai/compare/v0.5.0...v0.6.0
[0.5.0]: https://github.com/tanjirookamado602/sate-ai/compare/v0.4.0...v0.5.0
[0.4.0]: https://github.com/tanjirookamado602/sate-ai/compare/v0.3.0...v0.4.0
[0.3.0]: https://github.com/tanjirookamado602/sate-ai/compare/v0.2.0...v0.3.0
[0.2.0]: https://github.com/tanjirookamado602/sate-ai/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/tanjirookamado602/sate-ai/releases/tag/v0.1.0
