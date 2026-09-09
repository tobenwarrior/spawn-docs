# Authentication

## Local setup

The prototype runs the website at `http://localhost:3003` and a separate account service on `127.0.0.1:3002`. Requests to `/api/auth`, `/api/account` and `/api/v1` pass through the website origin. Run `npm run dev` from the repository to start both services.

Google OAuth credentials are not configured. Set `GOOGLE_CLIENT_ID` and `GOOGLE_CLIENT_SECRET` in `.env.local` using the keys documented in `.env.example`, then restart both services. Register `http://localhost:3003/api/auth/callback/google` as the callback and `http://localhost:3003` as the authorized JavaScript origin. The secret is server-only.

The frontend uses the Better Auth client to begin Google sign-in and read the current session. `GET /api/auth/status` reports whether the provider is configured. A Google login creates an account, not a cryptocurrency wallet. No fake development login endpoint is provided.

## Session-protected requests

Send same-origin credentials. Private `/api/v1` routes derive the user from the server session; they do not accept a user ID as authority. JSON writes require the accepted Origin header. A missing session returns 401 and an unacceptable write origin returns 403.

Current shared services are limited to the first-party application. Third-party builds must not receive its cookies. Before they are supported, the platform needs separate game origins and short-lived, game-scoped credentials.

## Wallet linking

Wallet linking attaches an existing externally owned address to an account. It does not create a session independently or authorize a payment.

| Method | Endpoint | Request / response |
| --- | --- | --- |
| GET | `/api/account/wallet` | `{ wallet }`, with null when no wallet is linked |
| POST | `/api/account/wallet/challenge` | Send `address`, `chainId`; receive `nonce`, `message` |
| POST | `/api/account/wallet/verify` | Send `nonce`, `signature`; receive `{ wallet }` |

Sign the exact returned message with the selected wallet. Challenges expire after five minutes, bind the account and session to the address and domain, and are consumed by a verification attempt. Request a new challenge after an invalid or expired proof.

An account may have one linked address; an address cannot be linked to two accounts. Replacing a linked address and smart-contract wallet verification are not implemented. The recorded chain ID comes from the wallet proof and is not evidence that tokens are deployed or that a balance was indexed.

## The first-party game window

Launching Rob the Rich requests a popup on the same origin. Browser cookie scoping preserves any current Spawn session without copying a token or cookie into the game URL. The launch requests `noopener` and `noreferrer`; the game has no opener reference. The current practice build still does not consume the account or save API. This is limited to the reviewed first-party build; third-party games must use separate origins and scoped credentials.

## Handling failure

Handle cancelled wallet prompts, expired sessions and unavailable services explicitly. Do not interpret a failed profile or wallet request as proof that the account has no data. Keep provider secrets and signing keys out of game bundles.

The [API reference](api.md) describes profile, project and save routes. The [SDK guide](sdk.md) covers the supported same-origin storage client.
