<!--
Sync Impact Report
Version change: template → 1.0.0
Modified principles: placeholder template → defined five actionable principles
Added sections: Project Constraints, Development Workflow
Removed sections: none
Templates requiring updates: ✅ .specify/templates/plan-template.md (generic, no update required)
Templates requiring updates: ✅ .specify/templates/spec-template.md (generic, no update required)
Templates requiring updates: ✅ .specify/templates/tasks-template.md (generic, no update required)
Follow-up TODOs: none
-->

# RSSFeedReader Constitution

## Core Principles

### I. MVP Simplicity
Deliver the minimum viable subscription management experience first. For MVP, the system MUST only support adding a feed URL and displaying the updated subscription list. No feed fetching, parsing, persistence, or URL validation is allowed until Extended-MVP.

### II. Safe Local Boundaries
Keep the prototype local and narrow the attack surface. Treat subscription URLs as opaque text, do not render untrusted feed content as HTML, and avoid any network or persistence complexity during MVP implementation.

### III. Maintainable Separation
Keep frontend and backend responsibilities explicit and small. The backend MUST expose a minimal API for subscription add/list operations, and the frontend MUST own input handling and list presentation. This separation must support future feed fetching, persistence, and background work without rewriting core subscription logic.

### IV. Quality and Verifiability
Write code that is easy to understand, easy to verify, and easy to extend. Implementation MUST favor explicit behavior over clever shortcuts, preserve a single source of truth for subscription state, and keep user-visible behavior deterministic.

### V. Documented Configuration
Document configuration, port coordination, and cleanup requirements as part of development. Before advancing beyond the MVP, verify local port settings, CORS policy, routing cleanup, and the absence of template demo pages.

## Project Constraints
The project is a local single-user RSS/Atom subscription proof-of-concept running on Windows, macOS, or Linux. Use ASP.NET Core Web API for backend responsibilities and Blazor WebAssembly for frontend presentation. For MVP:
- Store subscriptions in memory only
- Do not fetch or parse feeds
- Do not validate feed URLs
- Keep the UI minimal and functional
- Coordinate backend port, frontend port, and frontend API base URL explicitly

## Development Workflow
Before implementing feature code, complete cleanup and verification steps:
- Remove example Blazor demo pages that conflict with the MVP route structure
- Ensure only one root route (`@page "/"`) exists in the frontend
- Confirm frontend, backend, and appsettings port configuration match
- Verify backend and frontend launch successfully with no ambiguous route errors
- Use the stakeholder checklist to confirm the app is ready for local MVP testing

## Governance
This constitution is the authoritative source for RSSFeedReader development priorities. Amendments MUST be recorded by updating this file and bumping the constitution version.
- Patch version bumps apply to clarifications, wording fixes, and non-semantic refinements
- Minor version bumps apply to new principles, new constraints, or material expansion of guidance
- Major version bumps apply to principle removal, principle redefinition, or governance changes that alter how the project is managed

All PRs and reviews MUST include a short compliance summary citing the relevant principle or workflow section. Any deviation from this constitution requires explicit approval from the project owner and a documented mitigation path.

**Version**: 1.0.0 | **Ratified**: 2026-06-24 | **Last Amended**: 2026-06-24
