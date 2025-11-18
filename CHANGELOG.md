# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.3.0] - 2025-11-18

### Added
- New job for Bahasa-Indonesia API health monitoring (`https://bahasa-indo.onrender.com/health`)
- Independent monitoring for the Bahasa-Indonesia language learning backend

## [1.2.0] - 2025-11-18

### Changed
- Temporarily disabled Bahasa-Bali API health checks (app on hold)
- Added clear comments in workflow file for easy re-enablement
- Persian-Chai API health checks continue to run normally

## [1.1.0] - 2025-11-09

### Added
- Support for monitoring multiple Render backend APIs simultaneously
- New job for Bahasa-Bali API health monitoring (`https://bahasa-bali.onrender.com/health`)
- Independent job execution for each API for better visibility and granular monitoring
- Parallel execution of health checks for improved efficiency

### Changed
- Refactored workflow from single job to multiple independent jobs
- Updated workflow name from "Keep Render Backend Alive" to "Keep Render Backends Alive"
- Restructured README to document multiple API monitoring
- Enhanced monitoring section with instructions for viewing individual job statuses
- Improved customization documentation with examples for adding new APIs

## [1.0.0] - 2025-11-04

### Added
- Initial GitHub Actions workflow for keeping Render backend alive
- Health endpoint ping every 10 minutes to prevent Render free tier spin-down
- Automated health check for FastAPI backend at `https://language-learning-platform-uyqh.onrender.com/health`
- Manual workflow dispatch option for testing
- Status code validation (200 = healthy, other = failure)
- Comprehensive README with setup and customization instructions
- CHANGELOG for tracking project changes
