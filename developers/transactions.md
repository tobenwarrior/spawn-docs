# Project credentials and game transactions

## Design contract, not a released API

This chapter describes the selected creator-controlled pool direction. Project keys, agent publishing, player charges, reward transfers and pool withdrawals are **not implemented**. The current SDK only offers reviewed first-party save storage. No real payments are enabled and no production domain is configured.

The creator controls its game's available pool and may distribute or withdraw it. Spawn protects account ownership and accounting integrity; it does not validate the honesty of every game result. This is a discretionary creator treasury, not protected prize escrow.

## Separate credentials and permissions

| Client | Credential | Intended authority |
| --- | --- | --- |
| Coding agent / developer CLI | Expiring key for one project and environment | Submit builds and request review; read build status |
| Browser game | Public project ID and short-lived player grant | Read permitted player data and request a Spawn payment confirmation |
| Game server | Separate project runtime key with explicit reward scope | Request player payments and distribute only that game's available pool within configured limits |
| Creator account | Fresh owner authentication and wallet confirmation | Create/revoke keys, change limits and withdraw that game's available pool |

A publishing key cannot move funds or bypass release review. Runtime keys have no default pool-withdrawal authority. Owner permissions need not be handed to a coding agent just because it writes the game. A creator can grant a runtime key the full available reward budget if desired, but that makes the whole available pool exposed to compromise of that key; a daily cap and expiry are safer defaults.

Keys bind server-side to project, owner, environment, scopes, expiration and revocation status. Store only digests of cryptographically random secrets, reveal the secret once and redact authorization headers from logs. Revoke new access immediately; delegated short-lived grants also need a version/revocation check. A public project ID is identification, never a secret.

Derive the project from the authenticated key, then enforce ownership for every referenced pool, release and resource. Reject a different pool ID even if the caller has a valid key. Test with two developers, two projects owned by the same developer and separate test/live environments. Never expose arbitrary database access to game servers.

## Coding agents and build isolation

Keep a limited publishing key in an ignored local environment file or supported secret store. A CLI reads it without printing it. Do not paste live secrets into chat, source files, SDK examples, URLs or browser bundles. Remote agents with access to a secret are trusted recipients, so minimize scope and lifetime.

SDK instructions describe architecture but do not make submitted code trustworthy. Builds must run in isolated disposable workers without platform credentials, runtime reward keys, custody signing keys or private database access. An agent submits a versioned artifact for review; Spawn controls its public release and listing. Reviewing a browser artifact does not approve arbitrary future behavior of an external backend.

## Player-approved payments

A game requests a platform payment intent specifying an allowed product or entry and approved pricing version. Spawn displays the game, price, asset, payment purpose, refund terms and creator-controlled-pool disclosure in a trusted platform surface. A Google session, wallet link or developer-supplied player ID is not spending permission.

After player approval, Spawn consumes a short-lived single-use authorization bound to player, project, asset, amount and payment intent. It atomically debits the player's available balance and credits that game's pool, plus any separately configured and disclosed fee account. No fee is selected in the prototype. A ten-token example with no fee transfers exactly ten tokens; it creates no new supply.

Any optional automatic-entry allowance must be deliberately approved, limited by project, total spend, expiry and number of uses, and revocable. A runtime key cannot create the player's approval. The SDK returns a committed receipt; the game must not treat a timeout as proof of payment failure or request a new charge blindly.

Failed admission after payment needs explicit handling. When terms require automatic refunds, keep enough funds unavailable to the creator until admission or its timeout, then credit the player once on failure. Otherwise do not advertise a platform-guaranteed admission refund. Product delivery, refund terms and failed-entry behavior must be resolved before real charges are enabled.

## Rewards at the creator's discretion

The intended runtime interface can transfer an explicit amount to a valid Spawn player from the authenticated game's pool. It does not accept an arbitrary source pool, debit another player, mint a balance or call a custody signer. Event references are useful audit metadata; they do not prove truthful gameplay.

```ts
// Proposed game-server interface: not present in the released SDK.
const receipt = await server.rewards.transfer({
  recipientPlayerId,
  amountBaseUnits: '10', // Integer base units, not ten whole tokens.
  idempotencyKey: 'match-123:reward-event-456',
  reference: { matchId: 'match-123', eventId: 'reward-event-456' },
});
// Display a credited reward only after the platform confirms commitment.
```

The source pool is derived from the key. Spawn checks scope, project status, available funds, configured limits and recipient eligibility, then records one balanced transfer. A payout of ten whole tokens requires conversion using the configured token decimals; never assume the string above represents ten tokens.

A developer can invent a kill or choose a preferred recipient. Under the chosen ownership model, this spends creator-controlled funds rather than creating a platform liability without backing. It can still harm or mislead players, so public claims and platform disclosures must describe the actual discretion. An authoritative server remains important for gameplay quality but is not evidence of an honest creator.

A credited player balance is no longer part of the pool. The creator cannot claw it back or withdraw it. Insufficient pool funds cause a failed transfer, not a negative pool or an unfunded promise. Killing another player never grants permission to debit that player's remaining account balance.

## Creator withdrawals

The authenticated owner can withdraw the full available game-pool balance to its verified destination. Require fresh authentication, explicit amount/destination confirmation, replay protection and rate/amount controls. Pool ownership must be checked independently of project IDs supplied by the browser. A runtime reward key alone cannot change the withdrawal destination or initiate a pool withdrawal.

Reserve an accepted withdrawal atomically so it is unavailable for simultaneous rewards or another withdrawal. A separate custody service signs approved transactions without sharing its keys with developers or game workers. Keep the withdrawal pending until its outcome is definitive; a network timeout is not proof that a transfer failed. Refund or release a reserve only after establishing that it cannot also be paid on-chain.

## Ledger and concurrency requirements

Use integer base units, immutable balanced journal entries and a single controlled transfer service. Separate player available funds, pool available funds and pending obligations. Correct errors with linked reversals under platform policy, not silent history edits or developer balance overrides.

Every value-moving operation has a scoped idempotency key and canonical request digest. An identical retry returns the recorded result; the same key with different parameters fails. Database uniqueness also prevents consuming one payment grant twice. Different idempotency keys cannot reuse a single-use player authorization. A creator may deliberately send multiple distinct rewards from its own available pool, subject to limits.

Serialize competing debits, pool rewards and withdrawals using database transactions and locks or atomic comparisons. A concurrent reward and withdrawal cannot both spend the same tokens. Persist receipts and notification outbox records with the journal operation so recovery can resend a notification without repeating a transfer.

Chain deposits require unique chain/transaction/log identities, confirmation/finality rules and reorganization handling. Reserve reconciliation counts player balances, creator pool obligations and pending withdrawals exactly once, against confirmed custody assets; a transfer between categories does not increase backing. Do not expose private user records to achieve this accounting.

## Release conditions and containment

Before live funds, implement adversarial tests for cross-project access, leaked/revoked credentials, changed-payload retries, reused payment grants, concurrent pool withdrawals and rewards, insufficient funds, admission refunds, crash recovery, fraudulent destination changes and chain reorganization. Set bounded initial exposure and verify backup restores and incident procedures. Separate pause controls for new payments, rewards and withdrawals; suspension must not silently confiscate player or creator balances.

An independent review is required before handling live assets. Automated scans do not establish that no financial loss is possible. A production database, journal access policy, custody signer, token configuration and operational owner are still required. Legal and commercial treatment of paid games and discretionary rewards must be assessed before offering them to players.

## References

- [OWASP: object-level authorization](https://owasp.org/API-Security/editions/2023/en/0xa1-broken-object-level-authorization/)
- [OWASP: business-logic security](https://cheatsheetseries.owasp.org/cheatsheets/Business_Logic_Security_Cheat_Sheet.html)
- [Stripe: idempotent request semantics](https://docs.stripe.com/api/idempotent_requests)
