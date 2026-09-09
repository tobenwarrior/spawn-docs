# Version history

## Version 0.1 — 9 September 2026

First maintained edition of the Spawn whitepaper. Establishes the product direction, player and creator roles, local architecture, proposed shared economy, transparency requirements and staged roadmap.

Records the local implementation of public profiles, people search, creator project records, managed save storage and the first-party SDK prototype. Separates those capabilities from pending OAuth configuration, GitHub publishing, third-party isolation and the unimplemented financial systems.

Token economics remain **not finalized**. No token terms, fundraising figures, deployment dates or production security assurances are introduced.

Organizes documentation into two collections: the **Whitepaper** explains the full high-level experience, including the proposed reward pool and the website publishing journey; **Developer Docs** cover authentication, APIs, SDK integration and code architecture. Reward funding sources and distribution terms remain proposed and not finalized.

Private account views reset when the signed-in account changes, preventing the previous account’s profile and project state from carrying over.

Adds the selected Spawnling logo in a yellow-green palette, a revised library layout with a bottom-aligned footer, and a separate-window request for the first-party game. Browser preferences can override the requested window; no account credentials are passed in its URL.

The public documentation source is maintained in `tobenwarrior/spawn-docs`, with `spawn-launchpad.gitbook.io/spawn-docs/` reserved for the free GitBook publication. Whitepaper and Developer Docs share one space as separate page trees.

## Maintaining the whitepaper

The Markdown files in `whitepaper/` are the canonical product document. The website renders those files directly, so the local document and site share the same content. Engineering setup details remain in the repository's technical documentation.

Every material change to product behavior, public interfaces, supported integrations, economics, operational responsibility or implementation status should update the relevant chapter and this history in the same change. Changes from proposed to implemented must include verification evidence in the development record.

GitBook publication must use these canonical files through the documentation-only repository. Avoid an independent, manually diverging copy. Repository history records the published documentation version.

The interface uses one consistent light theme with warm-white surfaces, charcoal typography, Robin Neon actions and neutral navigation selection states. The application folder is now `spawn-launchpad`; SDK source lives in the sibling `spawn-sdk` repository, with a separate `spawn-docs` publication mirror. These repository changes do not enable third-party hosting or constitute an npm release.

Defines the intended agent-assisted submission model and separated publishing, reward and owner-withdrawal permissions. Each game has a creator-controlled pool: player payments enter that pool, the creator may top it up, distribute rewards or withdraw available funds. The pool is not guaranteed prize escrow; credited player rewards cannot be reclaimed by the creator. Spawn enforces ownership and funded transfers without certifying game outcomes. These are design contracts, not released APIs or enabled financial services.
