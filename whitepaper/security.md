# Trust, safety and operation

## A reviewed platform

A game launchpad can reduce risk through identity, code review and controlled publishing. It cannot guarantee that every creator is honest or that every game is free of defects. A review is tied to a particular release and its stated behavior.

Before third-party publishing, Spawn needs a documented submission policy, artifact review, permission checks, reporting channels and a process to suspend harmful releases. Listings should distinguish a submitted project, a reviewed build and a published game. Those labels must correspond to actions the platform has actually completed.

## Trust boundaries

Client code is under the player's control. It must not decide financial balances or authorize rewards on its own. Developer-controlled servers are external callers and need scoped permissions; using the SDK is not evidence that every request is legitimate.

Untrusted game builds need isolation from the account application. Build workers must not access account databases or signing secrets. Platform administrators need narrowly scoped access, logged actions and a recovery process appropriate to the systems they operate.

The local prototype enforces account ownership on private records, uses origin checks for writes, limits request size and rate, and versions save updates. These controls are a starting point. They do not constitute an audit of a production custody system.

## Custody and administration

If Spawn holds deposited tokens and manages off-chain balances, users rely on its contract design, ledger and operational controls. The operator's ability to approve withdrawals, pause services, upgrade contracts or change supply must be documented before deposits are enabled.

Key custody, multisignature arrangements, emergency powers, external review and the withdrawal authorization model are not finalized. No governance token rights or decentralized voting system are established by this version.

## Privacy

Public handles and optional wallet links are published through the public API. Private authentication data and private projects are not. Users should understand that public wallet activity may be copied by third parties and cannot be made private by hiding a profile later.

Financial transparency must include all obligations while minimizing personal data exposure. Publication of every player's transaction history is not a prerequisite for transparent reserves, and the final disclosure design remains open.

## Readiness for a public service

Production operation requires backup and restore testing, monitoring, incident ownership, abuse handling and capacity limits. Third-party publishing additionally requires content and rights policies. Features involving real assets need appropriate legal review of the actual operating model and intended markets before launch.

The current release is local development software. It does not accept real deposits or claim that a production financial security review has been completed.
