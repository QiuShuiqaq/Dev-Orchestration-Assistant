---
name: dev-orchestration-assistant
description: Orchestrate software delivery by routing work to desktop, mobile, or web delivery skills. Use when the user wants a software-development orchestrator that classifies the product surface, picks the right delivery chain, and continues through design, implementation, testing, packaging, and cleanup after the spec is approved.
---

# Dev Orchestration Assistant

Use this skill as a thin orchestration layer for software delivery.

Its job is to classify software work into one of three platform chains and hand execution to the correct specialist delivery skill:

- `desktop-software-delivery`
- `mobile-software-delivery`
- `web-software-delivery`

## Classification Rules

### Desktop

Choose desktop when the product:

- runs as a local process on Windows, macOS, or Linux
- needs local file access, tray integration, or system-level behavior
- ships as an executable, installer, or desktop bundle

### Mobile

Choose mobile when the product:

- runs mainly on iOS, Android, mini program ecosystems, or specialized mobile-adjacent devices
- depends on mobile capabilities such as camera, push, bluetooth, biometrics, or store distribution
- ships as ipa, apk, aab, or a platform-specific mobile build

### Web

Choose web when the product:

- runs mainly in a browser or WebView
- is delivered by URL instead of installation
- ships as a web build, static assets, or a server-rendered web deployment

## Operating Pattern

1. Classify the software surface as desktop, mobile, or web.
2. Clarify the subtype only as much as needed to choose the correct delivery chain.
3. If the spec is not approved, stop at analysis and recommended next steps.
4. If the spec is approved, hand off to exactly one platform delivery skill.
5. Let that platform skill drive design, planning, implementation, testing, packaging, and cleanup.

## Handoff Rules

- desktop -> `desktop-software-delivery`
- mobile -> `mobile-software-delivery`
- web -> `web-software-delivery`

Do not mix multiple platform delivery skills for one request.

## Pause Conditions

Pause instead of continuing when:

- the runtime surface is still ambiguous
- the spec is incomplete or internally inconsistent
- packaging or release work requires credentials or accounts that are unavailable
- the request hides a major architecture decision that has not been approved

## Example Triggers

- "I want one skill that orchestrates desktop, mobile, and web software delivery."
- "Help me decide whether this should follow a desktop, mobile, or web delivery path."
- "The spec is approved. Continue with the right platform delivery chain."
