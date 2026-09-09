# Platform architecture

## Separate systems with explicit responsibilities

Spawn is organized around five areas: discovery, accounts, creator publishing, game services and the proposed economy. Each has a different trust boundary. A game page should not hold a database credential, a build runner should not access wallet signing keys and a public profile query should not expose authentication records.

## The local implementation

The web application presents the library and platform pages. A separate local Node service handles Better Auth sessions, wallet linking, profile records, creator projects and managed saves. The frontend proxies those requests through its own origin.

SQLite persists the local records. Data stores are separated by domain in the server code, and routes identify the current account from its session before reading or modifying private records. This is a development setup; no production availability or capacity claim is made.

The current Rob the Rich build is a reviewed first-party asset. Third-party builds must not inherit the application origin or its account cookies. Before accepting those builds, Spawn needs a separate game origin, constrained embedding where appropriate and short-lived credentials scoped to the approved game and player.

## The proposed publishing system

A GitHub App would give Spawn narrowly scoped access to repositories selected by a creator. Repository access is authorization to read and build that repository, not access to every repository in a developer's account.

Builds run untrusted developer code. They must execute in isolated, disposable workers with restricted resource use, network policy and no access to platform secrets or the production database. Build output should become an immutable artifact, with source commit, logs and review state attached to the release.

Published static files can be distributed separately from the account service. The build system, database and multiplayer servers should not all share one unrestricted process or machine.

## Game services

Managed storage is addressed by authenticated player, game and save key. The local implementation offers JSON reads and version-checked writes. It is suitable for prototyping preferences and progress; a client can edit its own submitted data.

Authoritative multiplayer rules and reward validation belong on a trusted server. Creators choosing external databases must maintain their own access controls. Selecting a storage preference in the creator workspace does not provision infrastructure.

## The proposed economy

The target is to keep ordinary game actions off-chain while using a token and custody contracts for deposits and withdrawals. A platform ledger would record the obligations owed to users. Confirmed chain events would credit deposits; approved withdrawal requests would reserve balances before an on-chain payout.

The exact contract design is not finalized. Restricting the platform's contract surface to deposits and withdrawals still leaves token supply controls, signing authority, replay prevention, finality, recovery and contract administration to resolve. An internal database balance is a claim managed by the platform, not a balance independently enforced by the blockchain.

These systems are not implemented in the local prototype. Their release criteria are described in [transparency](transparency.md) and [current status](status.md).
