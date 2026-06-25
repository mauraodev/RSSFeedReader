# API Contract: MVP RSS reader

## Backend API

### Add subscription

- Method: `POST`
- Path: `/api/subscriptions`
- Request body:
  - `url` (string) — an RSS/Atom feed URL
- Response:
  - `201 Created` on success
  - Body: `{"url": "<submitted-url>"}`

### List subscriptions

- Method: `GET`
- Path: `/api/subscriptions`
- Response:
  - `200 OK`
  - Body: `[{"url": "<feed-url>"}, ...]`

## Frontend contract

The Blazor frontend must provide:
- A text input for entering a feed URL
- A button to submit the new subscription
- A list view showing each added subscription URL

## MVP constraints

- No feed content is fetched or rendered
- No feed URL validation is required
- State is stored in memory only for the current runtime session
