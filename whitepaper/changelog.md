# Version history

## Version 0.1 — 9 September 2026

First maintained edition of the Spawn whitepaper. Establishes the product direction, player and creator roles, local architecture, proposed shared economy, transparency requirements and staged roadmap.

Records the local implementation of public profiles, people search, creator project records, managed save storage and the first-party SDK prototype. Separates those capabilities from pending OAuth configuration, GitHub publishing, third-party isolation and the unimplemented financial systems.

Token economics remain **not finalized**. No token terms, fundraising figures, deployment dates or production security assurances are introduced.

Organizes documentation into two collections: the **Whitepaper** explains the full high-level experience, including the proposed reward pool and the website publishing journey; **Developer Docs** cover authentication, APIs, SDK integration and code architecture. Reward funding sources and distribution terms remain proposed and not finalized.

Private account views reset when the signed-in account changes, preventing the previous account’s profile and project state from carrying over.

Adds a generated Spawn logo, a revised library layout with a bottom-aligned footer, and a separate-window request for the first-party game. Browser preferences can override the requested window; no account credentials are passed in its URL.

The owner created a GitBook site shell at `spawn-launchpad.gitbook.io/spawn-docs/`. A free-only Git Sync export is prepared; content synchronization is not yet configured.

## Maintaining the whitepaper

The Markdown files in `whitepaper/` are the canonical product document. The website renders those files directly, so the local document and site share the same content. Engineering setup details remain in the repository's technical documentation.

Every material change to product behavior, public interfaces, supported integrations, economics, operational responsibility or implementation status should update the relevant chapter and this history in the same change. Changes from proposed to implemented must include verification evidence in the development record.

A GitBook site shell exists; publishing the documentation content through Git Sync is not yet configured. If enabled, use these files as the source and avoid maintaining an independent, manually diverging copy. External publication and its version should be recorded here when they occur.

The interface uses one consistent light theme with neutral navigation selection states. The application folder is now `spawn-launchpad`; SDK source lives in the sibling `spawn-sdk` repository, with a separate `spawn-docs` publication mirror. These repository changes do not enable third-party hosting or constitute an npm release.
