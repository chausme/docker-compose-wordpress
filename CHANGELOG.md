# Changelog

## [3.0.0] - 2026-03-18

### Changed

- Refactored nginx proxy to use Docker service networking.
- Simplified Docker Compose service naming (breaking change).
- Improved nginx config.

## [2.0.0] - 2026-03-17

### Added

- PHP info page at `http://wp.local/version.php` to check the current PHP version and installed extensions.

### Changed

- Refactored PHP Dockerfile to a simplified version with reduced duplication, improved build performance, and maintainability.
- Updated MySQL version to 8.4.

### Removed

- Removed PHP 5.6 legacy support due to compatibility concerns.

## [1.2.0] - 2026-03-16

### Added

- PHP 8.3-8.5 support.
- Minimal PHP 5.6 support for legacy WordPress sites.

### Changed

- Modernized Docker Compose configuration
- Refreshed README

### Fixed

- YAML formatting

## [1.1.0] - 2023-03-17

### Added

- PHP 8.0 version support.

### Fixed

- Dockerfile `CMD` commands.

### Removed

- `docker-compose restart` mention from README

## [1.0.0] - 2023-03-15

### Added

- Working setup with an ability to switch between PHP versions (7.4, 8.1, 8.2).
- CHANGELOG file to track project changes.
