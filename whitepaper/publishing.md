# Publishing a game

## A creator workspace on the website

Creators should be able to manage a game through Spawn's website: connect its repository, configure a build, preview a release and submit it for review. Developer documentation supports the coding work; the publishing interface handles the release process.

The current Your games (local prototype) page saves a private project record to the creator's account. It accepts a game name, description, optional GitHub repository reference and a storage preference. Google sign-in must be configured locally before the workspace can be used.

## The intended journey

### 1. Create your project

Give the game a name and explain what players do in it. Identify the creator and prepare the artwork and information needed for a listing. Only actual published games should appear in the public library.

The local prototype saves the name and description. Artwork submission and public creator publishing are not yet available.

### 2. Connect GitHub

The intended connection will ask the creator to grant Spawn access to a selected repository through a GitHub App. The creator will choose what to share. The platform should record the source version associated with each release.

Today, entering a repository URL only saves that reference. It does not connect GitHub, prove repository ownership or grant access to the code.

### 3. Choose how the game runs

The initial direction is for Spawn to host the browser build and offer optional storage for supported player data. Creators can keep their own databases or game-specific backends. A real-time multiplayer game initially needs creator-operated servers; managed storage does not provide a multiplayer simulation.

The current storage selector records a preference. It does not provision a server or database.

### 4. Build and preview

The planned build service will create a playable preview from the selected source version. Creators should check loading, controls, account behavior and any external services before submission. A failed build should show a useful error and leave the previous release intact.

No build service or preview deployment is connected yet.

### 5. Submit a release

The intended review covers the release artifact, declared services, permissions and any proposed purchases or rewards. Review of one release does not approve unlimited future changes or guarantee that a creator cannot act dishonestly.

Submitting the local project record currently marks it **awaiting integration**. It does not mean a build was reviewed or deployed.

### 6. Publish and maintain

Once the publishing system exists, an approved release can receive a catalogue listing and a playable address. Creators should be able to track release status and submit updates. The platform needs a rollback path and a process to suspend harmful releases.

Creator profiles are intended to show their published games. Private drafts and unreviewed project records do not become public games automatically.

## Using the shared economy

Listing a game does not grant permission to issue rewards. A game that participates in the proposed economy needs separately approved transaction behavior and a funded reward budget. Players must be able to understand the price or earning conditions before acting.

The [reward pool](rewards.md) chapter explains the proposed funding model. The [Developer Docs](../developers/README.md) describe the current code and API boundaries.
