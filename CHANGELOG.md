# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2025-11-04

### Added
- Initial GitHub Actions workflow for keeping Render backend alive
- Health endpoint ping every 10 minutes to prevent Render free tier spin-down
- Automated health check for FastAPI backend at `https://language-learning-platform-uyqh.onrender.com/health`
- Manual workflow dispatch option for testing
- Status code validation (200 = healthy, other = failure)
- Comprehensive README with setup and customization instructions
- CHANGELOG for tracking project changes
