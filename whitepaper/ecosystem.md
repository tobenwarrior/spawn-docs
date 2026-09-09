# The ecosystem

## Players

Spawn is intended to feel like a game library first. Players can browse available games, open a title and return to games they enjoy. The current prototype contains Rob the Rich and session-only favorites.

The account direction is Google sign-in, followed by an optional wallet connection when a player needs blockchain functionality. A Google account does not automatically create a wallet. Linking a wallet requires proof of control through a signed message; linking alone does not deposit funds.

Players can choose a public handle and display name separate from their Google identity. Public profiles can appear in people search. Showing a linked wallet is a separate choice, and email addresses are excluded from the public API. A public wallet can expose on-chain activity, so it is not enabled by default.

## Creators

Creators build the games that give Spawn its purpose. The intended platform provides listings, identity integration, optional managed storage and a reviewed publishing workflow. Creators remain responsible for the design, assets and behavior of their games.

A game can use a creator-operated backend for multiplayer or other specialist logic. Managed storage is an option for supported data, not a requirement to move every database onto Spawn. Use of the platform economy would require the approved transaction interfaces even when other systems are hosted elsewhere.

The local creator workspace currently saves project descriptions, GitHub repository references and a storage preference. These are persistent planning records. Connecting repositories, building releases and publishing third-party games remain future work.

## Platform operator

Spawn operates the account system, catalogue and shared services. The intended responsibilities also include reviewing releases, keeping the publishing process reliable, handling reports and maintaining the platform's financial accounting once real assets are introduced.

Early operation is centralized. Public information can make that operation easier to inspect, but it does not remove the operator's privileges or make the platform decentralized.

## Rob the Rich

Rob the Rich is Spawn's first listed browser game and the initial integration candidate. Its existing artwork and game build are retained. The current practice experience does not award redeemable platform tokens.

The game's role is practical: establish the discovery and play experience, then use a real title to validate accounts, saving and release updates before opening the platform to other creators. The managed save API exists, but the shipped game has not yet been wired to it.
