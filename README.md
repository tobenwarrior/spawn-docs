# Spawn

## A shared home for independent browser games

Whitepaper · Version 0.1 · 9 September 2026

Spawn is a game platform where independent developers can publish browser games and players can discover them through one account. Its proposed economy uses a shared token across participating games, with deposits and withdrawals on Robinhood Chain and everyday activity handled by platform services.

The idea starts with the games. A player should be able to open a game, understand it and start playing before needing to understand wallets or blockchains. A developer should be able to build a distinctive game without rebuilding accounts, distribution and storage for every release.

Spawn brings these two experiences together: a game library for players and a publishing platform for creators. Developers can use shared services through an SDK while retaining control over their game code and, where needed, their own multiplayer servers and databases.

A common economy introduces a responsibility beyond hosting games. Players need to know who controls their balance, what backs it and how changes can be checked. Spawn's proposed transparency system combines public platform information with on-chain records and a separately maintained account ledger. Public profiles are one part of that system; reserve reconciliation and transaction authorization are separate requirements.

## Starting point

The project is currently a local prototype. **Rob the Rich** is the first and only listed game. The prototype includes a game library, account integration, public profile settings, people search, creator project records and a small managed save-data service. Google sign-in requires OAuth configuration before it can be used locally.

Token deposits, withdrawals, GitHub deployments and a financial ledger are not live. The transparency page reports those systems as unconfigured. Token supply, ticker, allocations, fees and other economic terms remain **not finalized**.

This whitepaper describes the product, its architecture and the conditions for progressing beyond the prototype. It is the maintained product reference; the [current status](whitepaper/status.md) page separates implemented capabilities from configuration work and planned systems.

## Reading this document

Players can begin with [playing and accounts](whitepaper/accounts.md), [using the token](whitepaper/token-flow.md) and [the reward pool](whitepaper/rewards.md). Creators can read [publishing a game](whitepaper/publishing.md) for the website workflow. Code, SDK integration and APIs are covered separately in the [Developer Docs](developers/README.md). Readers evaluating the project can start with [the opportunity](whitepaper/vision.md), [economics](whitepaper/economics.md), [transparency](whitepaper/transparency.md) and [the roadmap](whitepaper/status.md).

The document is versioned with the project. Material product changes should update the relevant chapter and [version history](whitepaper/changelog.md). No token sale, return, launch date or allocation is established by this document.
