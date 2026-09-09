# Current status and roadmap

Version 0.1 · 9 September 2026

Spawn is in local development. The table describes the current repository, not a public production service. Milestones are acceptance criteria rather than promised launch dates.

## Current implementation

| Area | Status | What this means |
| --- | --- | --- |
| Game library | Implemented locally | One listed title: Rob the Rich; original artwork retained |
| Game play | Implemented locally | Existing browser practice build; no redeemable rewards |
| Favorites and demo balance | Session-only demo | Not synced account data or a financial ledger |
| Google account integration | Configuration required | Better Auth and session handling exist; OAuth credentials are required |
| Wallet linking | Implemented locally | Signed proof attaches an existing wallet to a signed-in account; no funds move |
| Public profiles and people search | Implemented locally | Opt-in visibility, optional linked wallet, paginated public API |
| Creator workspace | Implemented locally | Private project records and repository references persist |
| GitHub connection and builds | Not configured / planned | No repository access, build worker or live deployment |
| Managed saves and SDK | Local foundation | Versioned JSON storage; separate public-source SDK repository; reviewed first-party game only; shipped game integration still pending |
| Transparency dashboard and API | Implemented locally | Explicitly unconfigured financial data; no reserve proof |
| Project keys and agent submissions | Designed, not implemented | Publishing credentials are separate from game runtime and financial authority |
| Creator-controlled game pools and transfers | Designed, not implemented | Player-approved payments, discretionary creator rewards and owner withdrawals; no real payments |
| Token, custody contracts and financial ledger | Planned | No issued platform token or deposit/withdrawal system |
| Multiplayer hosting | Creator-operated direction | Spawn does not provide real-time servers |
| Whitepaper | Implemented locally | Main whitepaper plus separate Developer Docs; versioned Markdown and GitBook-compatible contents |

## Milestone 1 — A complete first-party loop

Configure and verify Google sign-in, connect Rob the Rich to managed saves and test returning to the same progress across sessions. Confirm account recovery behavior and the boundaries between private account information and public profiles.

The milestone is met when a player can use the complete account-and-save flow with a real configured provider, and the integration has been verified against failure and stale-save cases.

## Milestone 2 — A creator can publish

Configure a GitHub App, isolate builds, establish artifact storage and separate game origins. Introduce game-scoped access to shared services, a reviewed release process and a way to roll back a published release.

The milestone is met when an independent creator can publish an approved browser game from a selected repository without receiving platform secrets or access to another game's private data.

## Milestone 3 — A testable shared economy

Finalize token parameters and the accounting specification. Build a double-entry ledger, test-chain deposit indexing, withdrawal authorization and replay-safe processing. Publish reproducible reconciliation snapshots with a documented privacy model.

The milestone is met when independent verification and failure testing can explain every test deposit, transfer and withdrawal, including retries and interrupted processing. Live assets require further operational, security and legal readiness.

## Milestone 4 — Operate an invite beta

Choose infrastructure using measured workload, validate restores and incident procedures, establish developer quotas and support, and invite a limited group of creators and players.

The milestone is met through reliable operation and completed creator integrations. Usage, retention and cost data from that stage should inform capacity, pricing and the economic design.

## Decisions still needed

The intended domain is spawn.family; registration and hosting are not configured by this work. A GitBook site shell exists at `spawn-launchpad.gitbook.io/spawn-docs/`; content synchronization remains pending and the owner requires free-only features. No VPS has been selected, and no public deployment of the new platform services has been made.

Token economics remain not finalized. Public claims should be updated only after the corresponding implementation, configuration and verification are complete.
