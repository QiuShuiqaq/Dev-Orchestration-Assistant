---
name: desktop-software-delivery
description: Deliver desktop software after the spec is approved. Use when the product is a native desktop app, cross-platform desktop app, or lightweight desktop tool and Codex should continue through design, implementation, testing, packaging, and cleanup with minimal supervision.
---

# Desktop Software Delivery

Use this skill after the product has already been classified as desktop software and the spec is approved.

This skill owns the desktop-specific delivery path. It should keep moving unless packaging needs credentials, signing material, or a major hidden product decision appears.

## Scope

Handle these desktop subtypes:

- native desktop
- cross-platform desktop
- lightweight desktop or script tool

## Default Flow

1. Confirm subtype and target operating systems.
2. Define desktop-specific design decisions.
3. Create an execution plan in slices.
4. Implement slice by slice.
5. Run tests and platform-relevant verification.
6. Produce packaging or distribution artifacts.
7. Run safe cleanup for garbage created during the work.
8. Report results, artifact paths, and blockers.

## Design Focus

Before implementation, define:

- packaging targets such as exe, msi, dmg, AppImage, deb, or a plain executable
- local data and config storage paths
- OS integration boundaries such as tray, notifications, autostart, or filesystem access
- update model if relevant
- native capability boundaries if using Electron, Tauri, or another bridge-based stack

Use `api-and-interface-design` when those boundaries need explicit contracts.

## Planning

Use `planning-and-task-breakdown` to create thin runnable slices.

Prefer slices like:

- shell app boot or CLI entrypoint
- core file or task logic
- platform integration boundary
- packaging configuration

## Implementation

Use `incremental-implementation` as the primary implementation skill.

Default stack guidance:

- lightweight tool -> Python, Go, Rust, or simple scripts
- cross-platform GUI desktop -> Tauri or Electron first, unless the repo already commits to another stack
- native desktop -> use the platform-native toolchain already chosen by the spec

## Testing And Verification

Always verify before claiming completion.

Use:

- project-native tests if present
- the smallest useful new tests if coverage is missing
- `debugging-and-error-recovery` if build or runtime issues block progress

For UI-heavy desktop apps:

- verify startup path
- verify key interactions
- verify file or permission behavior
- verify packaging command success when possible

## Packaging

Packaging is required for completion unless the user explicitly asks for code-only work.

Packaging expectations:

- lightweight tool -> single executable, script entrypoint, or reproducible package command
- Electron or Tauri app -> installer, bundle, or build output for target platform
- native desktop -> platform-native build artifact

Pause only if packaging requires unavailable signing certificates or external release credentials.

## Cleanup

Use `clear-development-garbage` at the end.

Preview first, then apply cleanup only in the safe cleanup scope.

## Final Output

Report:

1. desktop subtype
2. chosen stack and packaging target
3. implemented slices
4. test and verification results
5. artifact paths or package commands
6. cleanup results
7. remaining blockers
