# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/0.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

### Changed

### Deprecated

### Removed

### Fixed

## [0.2.0]

### Deprecated

- `s1:processing_datetime` in favor of `processing:datetime`
- `s1:product_timeliness` in favor of `product:timeliness_category` and `product:timeliness`
- `s1:resolution` in favor of `gsd`, `spatial_resolution` (raster extension), and/or `sar:resolution_range` `sar:resolution_azimuth` (SAR extension)
- `s1:product_identifier` in favor of `id` or links to source products (e.g. relation types `via` or `derived_from`)

## [0.1.0]

### Added

- Create an initial definition of the extension.

[Unreleased]: <https://github.com/stac-extensions/sentinel-1/compare/v0.2.0...HEAD>
[0.2.0]: <https://github.com/stac-extensions/sentinel-1/compare/v0.1.0...v0.2.0>
[0.1.0]: <https://github.com/stac-extensions/sentinel-1/tags/v0.1.0>
