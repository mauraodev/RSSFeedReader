# Tasks: MVP RSS reader

**Input**: Design documents from `/specs/001-rss-subscriptions/`

**Prerequisites**: `plan.md`, `spec.md`, `research.md`, `data-model.md`, `contracts/api.md`

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Initialize the web app structure and confirm the MVP scope.

- [ ] T001 Create backend project structure in `backend/`
- [ ] T002 Create frontend project structure in `frontend/`
- [ ] T003 [P] Review and finalize feature docs in `specs/001-rss-subscriptions/` (`spec.md`, `plan.md`, `research.md`, `data-model.md`, `contracts/api.md`, `quickstart.md`)

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Build the minimal backend API and frontend HTTP configuration required for subscription add/list operations.

- [ ] T004 Implement backend API routing and CORS configuration in `backend/Program.cs`
- [ ] T005 Create the `Subscription` model in `backend/Models/Subscription.cs`
- [ ] T006 Create in-memory subscription storage service in `backend/Services/SubscriptionService.cs`
- [ ] T007 Implement the subscriptions controller in `backend/Controllers/SubscriptionsController.cs`
- [ ] T008 Configure frontend API settings in `frontend/wwwroot/appsettings.json`
- [ ] T009 Configure frontend HTTP client registration in `frontend/Program.cs`
- [ ] T010 [P] Create the main frontend subscriptions page in `frontend/Pages/Subscriptions.razor`

**Checkpoint**: Backend and frontend are wired for the add/list subscription contract.

---

## Phase 3: User Story 1 - Add a feed subscription (Priority: P1)

**Goal**: Enable a user to add a subscription URL and submit it to the backend.

**Independent Test**: Enter a feed URL into the UI and verify the new subscription is sent to the backend and returned with a successful response.

- [ ] T011 [US1] Implement the frontend add-subscription form in `frontend/Pages/Subscriptions.razor`
- [ ] T012 [US1] Implement frontend submit logic and API POST call in `frontend/Pages/Subscriptions.razor`
- [ ] T013 [US1] Implement backend POST `/api/subscriptions` behavior in `backend/Controllers/SubscriptionsController.cs`
- [ ] T014 [US1] Ensure the subscription service stores the submitted URL in memory in `backend/Services/SubscriptionService.cs`

---

## Phase 4: User Story 2 - View current subscriptions (Priority: P2)

**Goal**: Show the current list of subscriptions in the UI while the app is running.

**Independent Test**: Load the subscriptions page and verify the backend GET response populates the list view.

- [ ] T015 [US2] Implement backend GET `/api/subscriptions` in `backend/Controllers/SubscriptionsController.cs`
- [ ] T016 [US2] Implement frontend retrieval of the subscription list in `frontend/Pages/Subscriptions.razor`
- [ ] T017 [US2] Render the returned subscription URLs in `frontend/Pages/Subscriptions.razor`

---

## Phase 5: User Story 3 - Local runtime state only (Priority: P3)

**Goal**: Keep subscription state in memory only and verify state resets when the app restarts.

**Independent Test**: Add subscriptions, restart the app, and confirm the list clears.

- [ ] T018 [US3] Ensure `SubscriptionService` uses only in-memory storage and does not persist data to disk or database in `backend/Services/SubscriptionService.cs`
- [ ] T019 [US3] Document the runtime behavior in `specs/001-rss-subscriptions/quickstart.md`

---

## Phase 6: Polish & Cross-Cutting Concerns

**Purpose**: Final cleanup, documentation, and project consistency checks.

- [ ] T020 [P] Update `frontend/Shared/NavMenu.razor` or `frontend/App.razor` to expose the subscriptions page if needed
- [ ] T021 [P] Add or update app launch notes in `specs/001-rss-subscriptions/quickstart.md`
- [ ] T022 [P] Verify backend and frontend port configuration and CORS settings in `backend/Program.cs` and `frontend/wwwroot/appsettings.json`
- [ ] T023 [P] Confirm the feature is still aligned with the constitution and MVP scope in `.specify/memory/constitution.md`

---

## Dependencies & Execution Order

### Phase dependencies
- **Phase 1** must complete before **Phase 2** begins.
- **Phase 2** must complete before any story work in **Phase 3+** begins.
- **Phase 3**, **Phase 4**, and **Phase 5** should be implemented in priority order, but they are designed to remain independently testable.
- **Phase 6** depends on all prior phases.

### Story dependencies
- **US1** depends on foundational backend and frontend wiring from Phase 2.
- **US2** depends on the add/list API contract implemented in Phase 2.
- **US3** depends on the state model from Phase 2 and the subscription flow from US1.

## Parallel Execution Examples

- Work on `backend/Program.cs` CORS configuration (`T004`) while another developer builds `frontend/wwwroot/appsettings.json` and `frontend/Program.cs` (`T008`, `T009`).
- Work on `backend/Models/Subscription.cs` and `backend/Services/SubscriptionService.cs` in parallel (`T005`, `T006`).
- After Phase 2, one developer can implement frontend POST logic (`T012`) while another implements backend GET logic (`T015`).

## Implementation Strategy

### MVP-first delivery
1. Complete Phase 1: initialize backend/frontend structure and confirm docs.
2. Complete Phase 2: wire the minimal backend API and frontend API client.
3. Complete Phase 3: implement the core add-subscription flow.
4. Stop and verify the add flow works independently.
5. Complete Phase 4: implement list rendering and ensure the page displays subscriptions.
6. Complete Phase 5: enforce in-memory runtime-only behavior and verify reset on restart.
7. Finish with Phase 6: polish documentation, navigation, and configuration consistency.

### Incremental validation
- Validate the add-subscription flow before proceeding to list rendering.
- Verify all runtime state remains in memory before final acceptance.
- Keep the MVP scope narrow by avoiding any persistence or feed fetching in this release.
