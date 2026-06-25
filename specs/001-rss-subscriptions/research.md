# Research: MVP RSS reader

## Decision Summary

The MVP RSS reader will be implemented as a local web application with an ASP.NET Core Web API backend and a Blazor WebAssembly frontend. The backend will expose a minimal add/list subscription API, and the frontend will render a simple subscription entry form plus the current in-memory list.

## Rationale

- Stakeholder documents describe a proof-of-concept focused on subscription management only.
- The chosen stack supports rapid MVP development while enabling later extension to feed fetching, persistence, and background polling.
- Keeping the MVP scope narrow avoids unnecessary complexity from URL validation, HTTP feed fetching, and data storage.

## Alternatives Considered

- Using a single-page static web app without backend logic: rejected because the stakeholder guidance expects explicit backend/frontend separation and a future-ready API contract.
- Adding persistence in MVP: rejected because the charter specifically defers persistence to Extended-MVP.
- Adding feed parsing and fetching in MVP: rejected because the MVP is strictly subscription management only.

## Conclusions

- Implement MVP using ASP.NET Core + Blazor WebAssembly
- Use in-memory subscription storage for the current session
- Expose API endpoints for add/list subscription operations
- Keep the frontend UI minimal and focused on the core subscription workflow
