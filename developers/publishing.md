# Publishing and hosting

## Create a project record

After signing in, open Your games (local prototype). Enter a game name, description, an optional HTTPS GitHub repository URL and your intended storage choice. Save the project to keep the record in the local account database.

Submitting a record marks it **awaiting integration**. This does not clone a repository, verify repository ownership, build a game or publish a listing. No deployment URL is produced. The local limit is 20 projects per account.

## The planned GitHub workflow

A future GitHub App connection will let a creator select repositories to share with Spawn. The platform will need isolated builds, preview artifacts, review state and release history before publishing can be enabled.

Each approved release should identify its source commit and immutable artifact. Changes need a new release, with a rollback path. A repository URL by itself proves neither ownership nor safe behavior.

## Where each part runs

| Part | Initial direction |
| --- | --- |
| Browser build | Spawn-managed static distribution after the publishing system is built |
| Account service | Shared Spawn service |
| Supported save data | Optional Spawn storage |
| Multiplayer and game-specific server | Creator-operated |
| External database | Creator-operated, if chosen |
| Builds | Isolated disposable workers, not the account server |

A managed database does not provide matchmaking, simulation or real-time multiplayer. Choose a game backend based on concurrent players, update frequency and latency requirements. No VPS or production capacity is provisioned by the current workspace.

## Before third-party launches

The platform needs game-origin isolation, scoped service credentials, content and dependency review, quotas, reporting and release suspension. Uploading an SDK or passing a build does not guarantee that a game cannot misbehave.

The economic integration is also future work. A developer must never write directly to platform token balances; any later purchase or reward interface needs its own authorization and accounting rules.
