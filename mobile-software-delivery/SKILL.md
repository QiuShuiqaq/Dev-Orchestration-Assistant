---
name: mobile-software-delivery
description: Deliver mobile software after the spec is approved. Use when the product is a native mobile app, cross-platform mobile app, mini program, or specialized mobile-device app and Codex should continue through design, implementation, testing, packaging, and cleanup with minimal supervision.
---

# Mobile Software Delivery

Use this skill after the product has already been classified as mobile software and the spec is approved.

This skill owns the mobile-specific delivery path. It should keep moving unless signing, store access, device-only verification, or a major hidden product decision blocks safe progress.

## Scope

Handle these mobile subtypes:

- native iOS or Android app
- cross-platform mobile app
- mini program or quick app
- specialized wearable, TV, or automotive app

## Default Flow

1. Confirm subtype and target platforms.
2. Define mobile-specific design decisions.
3. Create an execution plan in slices.
4. Implement slice by slice.
5. Run tests and platform-relevant verification.
6. Produce build artifacts or packaging outputs.
7. Run safe cleanup for garbage created during the work.
8. Report results, artifact paths, and blockers.

## Design Focus

Before implementation, define:

- capability matrix for camera, location, push, bluetooth, auth, payments, or offline support
- platform difference boundaries
- native bridge or plugin points for cross-platform stacks
- signing and release path
- store or platform review constraints when relevant

Use `api-and-interface-design` when module or bridge contracts need explicit boundaries.

## Planning

Use `planning-and-task-breakdown` to create thin slices that remain testable.

Prefer slices like:

- app shell and navigation
- core feature flow
- platform capability integration
- release or packaging configuration

## Implementation

Use `incremental-implementation` as the primary implementation skill.

Default stack guidance:

- deep platform integration or top-tier performance -> native
- one shared team across iOS and Android -> Flutter first unless the repo already commits elsewhere
- mini program or China-first ecosystem reach -> uni-app or Taro when the spec favors that distribution model

## Testing And Verification

Always verify before claiming completion.

Use:

- project-native tests if present
- emulator or simulator verification when possible
- the smallest useful new tests if coverage is missing
- `debugging-and-error-recovery` if build, runtime, or bridge issues block progress

For web-like mobile surfaces or embedded pages, use `playwright` only when it fits the actual runtime surface.

## Packaging

Packaging is required for completion unless the user explicitly asks for code-only work.

Packaging expectations:

- native or cross-platform mobile app -> ipa, apk, aab, or reproducible build command
- mini program -> upload-ready build output or platform build command
- specialized device app -> build artifact appropriate for the target ecosystem

Pause only if packaging requires unavailable signing certificates, app-store accounts, or protected release credentials.

## Cleanup

Use `clear-development-garbage` at the end.

Preview first, then apply cleanup only in the safe cleanup scope.

## Final Output

Report:

1. mobile subtype
2. chosen stack and release target
3. implemented slices
4. test and verification results
5. artifact paths or package commands
6. cleanup results
7. remaining blockers
