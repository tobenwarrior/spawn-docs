# Public API and SDK reference

Version 1 · Local prototype

Requests use the website origin. In local development the web application proxies `/api/v1` to the account service. Financial quantities are unavailable; future token amounts must use integer strings in the smallest token unit.

## Public reads

| Method | Path | Result |
| --- | --- | --- |
| GET | `/api/v1/search?type=games&q=` | Matching catalogue games; currently Rob the Rich only |
| GET | `/api/v1/search?type=people&q=&cursor=` | Public profiles, with a `nextCursor` when another page exists |
| GET | `/api/v1/people/{handle}` | Public profile, or 404 |
| GET | `/api/v1/transparency` | Configuration status and unavailable financial fields |
| GET | `/api/v1/transparency/snapshots` | Unconfigured status, empty `items`, null `nextCursor` |

Search queries allow up to 80 characters. People search returns up to 25 profiles per page, sorted by handle; pass the returned cursor unchanged with the same query. These pages are not a consistent financial snapshot, and private accounts are excluded.

Public profiles contain a separate public ID, handle, display name, biography and profile timestamps. A linked wallet appears only when its owner enables disclosure. Balance fields remain null and `games` is currently empty because creator projects cannot yet be published. Emails and private account identifiers are excluded.

## Signed-in account routes

| Method | Path | Body / result |
| --- | --- | --- |
| GET | `/api/v1/account/profile` | Own profile and visibility settings, or null |
| PUT | `/api/v1/account/profile` | `handle`, `displayName`, `bio`, `isPublic`, `showWallet` |
| GET | `/api/v1/projects` | Own projects and unconfigured GitHub/build status |
| POST | `/api/v1/projects` | `name`, `description`, `repository`, `storage` |
| POST | `/api/v1/projects/{id}/submit` | Marks an owned project `awaiting_integration` |
| GET | `/api/v1/game-storage/{gameId}/{key}` | Save value, version and timestamp, or null |
| PUT | `/api/v1/game-storage/{gameId}/{key}` | `value`, `expectedVersion` |

Handles start with a letter and use 3–24 lowercase letters, numbers or underscores. Display names allow 40 characters and biographies 300. A project name allows 60 characters and its description 500. Repository references, when provided, must be HTTPS GitHub repository URLs. Storage preference is `spawn` or `external`; it does not provision either service. Local accounts may create up to 20 projects.

Writes require a valid session and an accepted same-origin request. JSON bodies are limited to 16,384 bytes and reject unknown fields. The local API applies an in-memory limit of 120 requests per minute per client address. Production distributed rate limiting is not implemented.

Typical errors use `{ "error": "message" }`: 400 for invalid input, 401 for no session, 403 for an unacceptable origin, 404 for missing or inaccessible records, 409 for conflicts and 429 for limits. Clients should handle service failures rather than interpreting them as empty data.

## Managed save example

The private workspace package exports `createSpawnClient`. The following illustrates a reviewed first-party integration; it is not a third-party production credential flow.

```ts
import { createSpawnClient } from '@spawn/sdk';

const spawn = createSpawnClient('rob-the-rich');
const previous = await spawn.load<{ sound: boolean }>('settings');
const saved = await spawn.save(
  'settings',
  { sound: false },
  previous?.version ?? 0,
);
```

Version zero creates a new save. Later writes use the last returned version. A conflict means the caller should reload and resolve the change, rather than silently overwriting it. A key uses 1–64 letters, numbers, underscores or hyphens. The current service allows 12,000 serialized bytes per value, 100 keys and 65,536 bytes per player per game.

Only `rob-the-rich` is enabled. Player identity comes from the session, not a caller-supplied user ID. This SDK cannot mint tokens, change financial balances or authorize rewards. The shipped game has not yet adopted the save client.

## Integration boundaries

There are no current APIs for initiating deposits, withdrawing tokens, receiving GitHub webhooks, uploading arbitrary builds or remotely querying all private accounts. A future release must document and test those interfaces before they are advertised as available.
