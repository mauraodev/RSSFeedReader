# Data Model: MVP RSS reader

## Entities

### Subscription
- `url` (string): the RSS/Atom feed URL entered by the user

## Relationships

- The MVP data model has a single entity: Subscription.
- Subscriptions are stored in a simple in-memory list on the backend.

## Validation Rules

- MVP assumes valid URLs are provided; explicit URL validation is not required.
- Duplicate detection is not required for MVP.

## State

- The subscription list is in-memory only and resets when the application restarts.
