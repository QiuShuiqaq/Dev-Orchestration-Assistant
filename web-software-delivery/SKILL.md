---
name: web-software-delivery
description: Deliver web software after the spec is approved. Use when the product is a traditional web site, SPA, PWA, or embedded web page and Codex should continue through design, implementation, testing, packaging, and cleanup with minimal supervision.
---

# Web Software Delivery

Use this skill after the product has already been classified as web software and the spec is approved.

This skill owns the web-specific delivery path. It should keep moving unless deployment access, missing environment details, or a major hidden product decision blocks safe progress.

## Scope

Handle these web subtypes:

- traditional multi-page site
- SPA
- PWA
- embedded web page or WebView content

## Default Flow

1. Confirm subtype and deployment model.
2. Define web-specific design decisions.
3. Create an execution plan in slices.
4. Implement slice by slice.
5. Run tests and browser-relevant verification.
6. Produce build or deployment-ready artifacts.
7. Run safe cleanup for garbage created during the work.
8. Report results, artifact paths, and blockers.

## Design Focus

Before implementation, define:

- routing model
- rendering model
- auth and API integration boundaries
- deployment target such as static hosting, CDN, or server runtime
- browser, responsive, offline, and WebView constraints when relevant

Use `api-and-interface-design` when frontend-backend contracts or public UI module boundaries need explicit design.

## Planning

Use `planning-and-task-breakdown` to create thin vertical slices.

Prefer slices like:

- app shell or page skeleton
- core user flow
- API integration
- build and deployment configuration

## Implementation

Use `incremental-implementation` as the primary implementation skill.

Default stack guidance:

- content or marketing site -> MPA or server-rendered site
- admin panel, SaaS app, online tool -> SPA first
- install-like or offline-first browser experience -> PWA

Use `react-best-practices` as a post-check when the stack is React or Next.js.

## Testing And Verification

Always verify before claiming completion.

Use:

- project-native tests if present
- `playwright` for browser verification when the product runs in a browser or WebView
- the smallest useful new tests if coverage is missing
- `debugging-and-error-recovery` if runtime or build issues block progress
- `web-design-guidelines` as a post-check when UI or accessibility quality matters

## Packaging

Packaging is required for completion unless the user explicitly asks for code-only work.

Packaging expectations:

- static web app -> production build output
- server-rendered or full-stack web app -> reproducible production build and start path
- embedded web page -> deployable assets or host-app integration build output

Pause only if deployment or release packaging requires unavailable environment secrets or infrastructure access.

## Cleanup

Use `clear-development-garbage` at the end.

Preview first, then apply cleanup only in the safe cleanup scope.

## Final Output

Report:

1. web subtype
2. chosen stack and deployment target
3. implemented slices
4. test and verification results
5. artifact paths or build commands
6. cleanup results
7. remaining blockers
