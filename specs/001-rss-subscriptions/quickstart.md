# Quickstart: MVP RSS reader

## Prerequisites

- .NET 8 SDK installed
- A browser for running the Blazor WebAssembly frontend

## Setup

1. Open the repository in your development environment.
2. Ensure the project contains a backend API project and a Blazor frontend project.
3. Confirm backend and frontend ports are set consistently in:
   - backend launch settings
   - frontend launch settings
   - `wwwroot/appsettings.json`

## Run the app

1. Start the backend API.
2. Start the Blazor WebAssembly frontend.
3. Open the frontend app in the browser.
4. Add a feed URL in the input field and click Add.
5. Confirm the new URL appears in the subscription list.

## Verification

- The app must display the URL list immediately after submission.
- The app should not attempt to fetch feed content.
- Restarting the app should clear the list, proving in-memory state only.

## Notes

- This MVP does not validate URLs or persist subscriptions.
- External feed retrieval is out of scope for this phase.
