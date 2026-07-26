# test-versioning

A test repository for understanding GitHub tags and releases.

## Purpose

This repository is used to experiment with and understand:
- GitHub Actions workflows
- Semantic versioning
- Automated tag creation and management
- GitHub releases

## CI/CD Workflow

This repository uses a GitHub Actions workflow that:
1. Runs on push to `main` branch
2. Uses semantic versioning to automatically calculate the next version based on commit messages
3. Creates and pushes version tags to the repository

### Commit Message Conventions

The workflow uses the following conventions for versioning:

- **Major version bump**: Include `/!:` or `BREAKING CHANGE:` in your commit message
- **Minor version bump**: Include `feat:` or `feat(scope):` in your commit message
- **Patch version bump**: Regular commits (default)

Example commit messages:
```
feat: add new feature  # Minor version bump
fix: resolve bug       # Patch version bump
feat!: breaking change # Major version bump
BREAKING CHANGE: major update  # Major version bump
```

## Getting Started

1. Clone this repository
2. Make commits following the conventions above
3. Push to the `main` branch
4. The GitHub Actions workflow will automatically calculate the version and create a tag
