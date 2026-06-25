# Implementation Plan: MVP RSS reader

**Branch**: `[001-rss-subscriptions]` | **Date**: 2026-06-24 | **Spec**: `spec.md`

**Input**: Feature specification from `/specs/001-rss-subscriptions/spec.md`

**Note**: This file is the implementation plan for the MVP RSS reader and is paired with the feature spec.

## Summary

Build a local MVP RSS reader that supports only subscription management: adding feed URLs and displaying the current list in the UI. The architecture uses an ASP.NET Core Web API backend to manage a simple in-memory subscription list and a Blazor WebAssembly frontend to capture URLs and render the subscription list.

## Technical Context

**Language/Version**: C# / .NET 8+ (ASP.NET Core Web API, Blazor WebAssembly)

**Primary Dependencies**: ASP.NET Core, Blazor WebAssembly, `System.Net.Http`, `Microsoft.AspNetCore.Cors`, xUnit/bUnit for test scaffolding

**Storage**: In-memory collection of subscription URLs; no persistence for MVP

**Testing**: xUnit for backend unit tests, bUnit for frontend component tests, optional integration tests using the local API contract

**Target Platform**: Local cross-platform development on Windows, macOS, and Linux; browser-hosted frontend with local API backend

**Project Type**: Web application with separate backend and frontend projects

**Performance Goals**: Responsive local UI; immediate add/list behavior for subscriptions; no perceptible delay on local development hardware

**Constraints**: No feed fetching, parsing, or validation in MVP; no persistence beyond the current runtime session; local single-user proof-of-concept only

**Scale/Scope**: Single-user local MVP; subscription management only; extends later to feed fetching and persistence in Extended-MVP

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

- Principle I: MVP simplicity — this plan keeps the scope strictly limited to subscription management and no feed retrieval.
- Principle II: Safe local boundaries — the MVP will treat submitted URLs as opaque text and will not render external feed content.
- Principle III: Maintainable separation — the backend exposes a clean add/list API and the frontend owns UI state and rendering.
- Principle IV: Quality and verifiability — the plan emphasizes explicit behavior, a minimal API contract, and testable acceptance criteria.
- Principle V: Documented configuration — the plan includes port coordination and launch guidance in quickstart.md.

## Project Structure

### Documentation (this feature)

```text
specs/001-rss-subscriptions/
├── plan.md
├── research.md
├── data-model.md
├── quickstart.md
├── contracts/
│   └── api.md
└── tasks.md
```

### Source Code (repository root)

```text
backend/                          # ASP.NET Core Web API project
frontend/                         # Blazor WebAssembly frontend project
```

**Structure Decision**: The project is a web application with explicit frontend/backend separation. The current repository root does not yet contain these source directories, so they will be created as the feature is implemented.

## Complexity Tracking

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
| None      | N/A        | The plan maintains MVP simplicity and avoids unnecessary architecture complexity |
