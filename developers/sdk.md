# SDK and managed storage

## Current availability

`@spawn/sdk` is a TypeScript prototype maintained in the separate public-source [spawn-sdk repository](https://github.com/tobenwarrior/spawn-sdk). It has not been published to npm. It exposes a same-origin client for reviewed first-party code; only `rob-the-rich` is enabled by the server.

Do not run arbitrary third-party builds on Spawn's account origin to make this client work. Separate game origins and game-scoped authorization are prerequisites for broader integration.

## Load and save

```ts
// Import the local SDK source through your TypeScript bundler.
import { createSpawnClient } from './path/to/spawn-sdk/src/index';

const client = createSpawnClient('rob-the-rich');
const existing = await client.load<{ sound: boolean }>('settings');

try {
  const saved = await client.save(
    'settings',
    { sound: false },
    existing?.version ?? 0,
  );
  // Keep saved.version for the next update.
} catch (error) {
  // Show the failure; reload and resolve conflicts before retrying.
}
```

Player identity comes from the signed-in session. Do not pass a user ID or store database credentials in the game. A missing save returns null. A successful write returns `value`, `version` and `updatedAt`.

## Versions and limits

Use version zero to create a save. An update must supply the current version as `expectedVersion`; a stale version receives HTTP 409. Reload before deciding how to merge or retry the change.

Values must be JSON, up to 12,000 serialized bytes each. The local limit is 100 keys and 65,536 serialized bytes per player per game. Keys contain 1–64 letters, numbers, underscores or hyphens. HTTP request bodies also have a 16,384-byte limit.

The service stores player-controlled data. It does not validate your game's schema, prevent cheating or turn progress into an authorized financial reward. Include a schema version in evolving game saves and validate data when loading it.

## Not yet provided

There is no SDK method for spending tokens, awarding withdrawable rewards, deploying a build or running a multiplayer server. Rob the Rich's shipped practice build is not yet connected to this save client. The [API reference](api.md) documents all currently available platform routes.

## Proposed next integration

The planned SDK separates browser, agent-publishing and game-server clients. Private project keys never belong in the browser. See [project credentials and game transactions](transactions.md) for the proposed permission model and creator-controlled pool transfer contract; none of those methods is released yet.
