# Game reward pools

## A treasury controlled by each creator

Every game is intended to have its own creator-controlled token pool. The creator can add tokens, receive player payments, distribute rewards to Spawn accounts or withdraw the pool's available balance. One game's pool is separate from every other game and from player account balances.

This is the selected product direction, not a live financial service. No pool is funded or operating in the prototype. Token supply, fees, allocations and reward formulas remain **not finalized**.

## Funding a pool

A creator can top up the pool to encourage participation. When a player approves a purchase or entry payment, that payment transfers tokens from the player's available Spawn balance to the game's pool under the disclosed terms. For a simple ten-token example with no fee, the player's balance decreases by ten and the pool increases by ten in one transaction. Ten tokens is an illustration, not a fixed platform entry price.

Under this model, a completed payment becomes creator-controlled funds. It is not held in a protected match prize account. Players must be told what they are buying, whether a refund is available, and that the payment does not guarantee a reward. Any future platform fee must be separately disclosed and recorded; no fee is selected here.

## How rewards work

The creator decides the game's reward rules and when to distribute tokens from its available pool. A game server may ask Spawn to credit a player after a kill, win or other event. Spawn verifies the calling credential, the game pool, the recipient and the available funds, then records the transfer exactly once.

Spawn does not certify that the reported gameplay result is honest. A developer can favor recipients or invent results while distributing its own available funds. This discretion must not be presented as a platform guarantee of fair outcomes.

A successful reward reduces the game pool and increases the player's Spawn balance atomically. Once credited, the reward belongs to the player: the creator cannot withdraw it, reverse it at will or use it to fund another award. A displayed score, projected earning or unconfirmed SDK request is not a credited token balance.

## What the creator can withdraw

The creator can request withdrawal of all available, uncommitted funds in its game pool. Tokens already credited to players, reserved for an accepted withdrawal or committed by an explicit refund/transfer obligation are unavailable for another withdrawal. Pending operations cannot double-spend the same funds.

No match-level reserve is required by this selected model. A future campaign that promises a protected prize would need a separate locked arrangement and different disclosures; it cannot simultaneously promise guaranteed prizes and unrestricted creator withdrawal.

## What players should see

Each paid game should clearly state: **Creator-controlled pool. The creator can distribute or withdraw available tokens. Pool size does not guarantee a payout.** Spawn's payment confirmation must show the price, game, payment purpose and applicable refund/reward terms before the player approves.

The public pool page should show the available balance, creator top-ups, player-payment totals, credited rewards and creator withdrawals, with a timestamp. A large balance is a snapshot, not a guaranteed future budget or proof that the game is trustworthy. Reports, moderation and suspension remain possible; creator control does not excuse deceptive listings or false claims about Spawn protections.

## Accounting and current availability

A transfer from a player into a pool changes who is entitled to the tokens; it does not create new underlying tokens. A transfer from a pool to a player changes that entitlement again. Both player balances and creator pool obligations must be covered by the platform's reserve accounting, including pending withdrawals without double-counting.

No guaranteed earnings, yield, prize or airdrop allocation is announced. Rob the Rich is currently a practice build with no entry charge or redeemable rewards. Its use as an example does not mean the financial integration exists.
