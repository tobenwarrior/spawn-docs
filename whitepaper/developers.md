# Building on Spawn

## The intended publishing experience

A creator connects a GitHub account, grants access to a selected repository and chooses how the game should run. Spawn builds a release, gives the creator a preview and reviews the release before making it available in the catalogue.

Each published release should correspond to an identifiable source commit and build artifact. Updating a game should create a new release that can be reviewed and rolled back. A successful first review cannot guarantee the safety of every later update.

This workflow is the target. The current creator workspace records a repository URL and saves projects to the local database. It does not request GitHub access, clone repositories or execute builds. A submitted project is marked **awaiting integration**, with no deployment URL.

## Shared services and developer choice

| Component | Spawn's direction | Creator's role |
| --- | --- | --- |
| Game frontend | Hosted, versioned browser builds | Build and maintain the game |
| Player identity | Shared account integration | Request only the scopes the game needs |
| Save data | Optional managed storage | Define and validate the game's save format |
| Multiplayer | Creator-operated initially | Host matchmaking and authoritative game servers |
| Specialist database | Optional external service | Operate it and protect its credentials |
| Platform token activity | Approved platform transaction API, planned | Submit authorized actions; never edit account balances directly |

A save-data service is not a multiplayer server. Real-time games still need synchronization, latency management and authoritative rules. Spawn does not currently provide those systems or allocate a VPS to every developer.

## The SDK

The local `@spawn/sdk` package contains a small TypeScript client for loading and saving game data. It is a private workspace prototype, not a published npm package. The current transport uses the signed-in player's same-origin session and only permits the reviewed first-party game identifier `rob-the-rich`.

A save has a version. Updating it requires the version last read, so a stale tab cannot silently overwrite a newer save. The current limits are 12,000 serialized bytes per value, 100 keys and 65,536 serialized bytes per player per game.

A future third-party SDK needs game-scoped credentials and origin isolation before this access pattern can be opened to arbitrary games. A developer-supplied game ID is not an authorization boundary by itself.

## How integration is enforced

Possessing an SDK does not prove a game routes all activity through Spawn. A client library can be changed or bypassed. Enforcement belongs at the service boundary: authenticate the caller, identify the approved game, authorize the action, validate its inputs and record the result.

A creator may use external services for features the platform permits. They must not be able to create redeemable account balances through those services. The future economy API must accept only approved transaction types backed by authoritative evidence. Browser-reported scores and save files are not sufficient evidence for financial rewards.

## Working with coding agents

The repository's developer guide provides integration instructions for people and agents. Game projects should separate interface code, game rules, service adapters, assets and server code where applicable. Secrets belong on a server. Generated code receives the same review as handwritten code.

The aim is an understandable codebase that can grow with the game, rather than a required number of files or a particular engine. A small prototype can stay small; unrelated responsibilities should not accumulate in one document.

See the [API reference](../developers/api.md) for the local interfaces and [architecture](architecture.md) for the boundaries required before third-party hosting.
