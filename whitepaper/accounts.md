# Playing and your account

## Start with the game

Open the game library (local prototype) and choose Rob the Rich, the first and only listed title. Play requests a separate game window; browser preferences may still open a tab. A fallback link is available if the window is blocked. Its practice build can be played as a guest. You do not need a wallet or tokens to try it.

The heart beside the title adds it to Favorites for the current page session. Favorites and the demonstration balance reset on reload. The shipped game is not yet connected to account-based saving.

## One Spawn identity

The account direction is Google sign-in followed by an optional wallet link. A Google account does not automatically create a wallet. Local OAuth configuration is still required before Google sign-in becomes available.

After signing in, open account settings (local prototype) to choose a public identity. Your Spawn display name can differ from your Google name.


## Your profile

After signing in, open account settings (local prototype). Choose a handle of 3–24 letters, numbers or underscores, beginning with a letter. Handles are lowercase and unique. Your display name can use up to 40 characters; your biography can use up to 300.

Enable **Make my profile public** if you want a profile page that other people can find through People (local prototype). Leave it off to keep your profile out of public search. Your Google email is not published as part of the profile.

## Showing a wallet

**Show my linked wallet** is a separate setting, off by default. When both public visibility and wallet disclosure are enabled, your verified wallet address and chain ID can appear on your profile and in the public API.

Blockchain activity at a public wallet address can be inspected by anyone. Hiding the address later prevents future disclosure through your profile, but cannot erase copies other people have already made.

## Games and balances

Profile pages include space for published games and balance information. Creator publishing and real token accounting are not available yet, so no published creator games or financial totals are shown. An unavailable balance does not mean a verified zero balance.

A public profile is not a guarantee that a creator or their game is trustworthy. It is one way to identify who is behind a release.

## Linking a wallet

The wallet control in account settings asks a supported browser wallet to sign a message proving address ownership. It does not transfer tokens. The platform does not ask for the player's seed phrase or private key.

The current implementation supports one linked externally owned address per account. Replacement and smart-contract wallets are not yet supported. Connecting an address is separate from enabling its public visibility.

## Balances and earnings

The current PLAY balance is a simulation, not an issued token or a future allocation. The intended real token flow is explained in [Using the token](token-flow.md), and earning through funded campaigns is described in [The reward pool](rewards.md).
