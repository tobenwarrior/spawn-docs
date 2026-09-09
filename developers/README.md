# Developer documentation

## Build a browser game for Spawn

Spawn's developer platform is being built around browser games, a GitHub publishing workflow and optional shared services. You can use your own multiplayer server or database. The long-term aim is to let a creator go from a selected repository to a reviewed, playable release.

The local foundation currently includes private project records and a small versioned save-data API. It does not yet connect GitHub, execute builds or publish third-party games. The save transport is restricted to reviewed first-party code.

## Start here

1. Read [authentication](authentication.md) for sessions and wallet linking.
2. Read [project architecture](architecture.md) for a structure that works with people and coding agents.
3. Read [the SDK and storage guide](sdk.md) for the current integration and its boundaries.
4. Read [publishing and hosting](publishing.md) to understand what can be saved today and what still needs infrastructure.
5. Read [project credentials and game transactions](transactions.md) for the proposed agent, payment and pool-transfer boundaries. These financial interfaces are not released.
6. Use the [API reference](api.md) for exact routes, limits and errors.

The creator workspace (local prototype) records your game name, description, repository reference and storage preference. A signed-in account is required; local Google OAuth configuration is still pending.

For the wider product and economic direction, see the [Spawn whitepaper](../README.md).
