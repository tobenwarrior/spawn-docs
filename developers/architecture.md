# Project architecture

## Organize around responsibilities

A browser game can start small and still be easy to extend. Keep game rules separate from rendering and interface code, and put calls to Spawn behind an adapter. An example layout is:

```text
src/
  game/          # Rules, simulation and game state
  rendering/     # Scene, sprites and camera
  ui/            # Menus, HUD and accessibility
  services/      # Spawn adapter and external service clients
  schemas/       # Versioned save formats and validation
public/assets/   # Art and audio, with licenses
server/          # Optional authoritative multiplayer/backend
tests/          # Behavior and integration checks
```

Use the folders that have a real purpose for your game. The requirement is clear ownership of responsibilities, not a fixed file count. Avoid putting unrelated account logic, networking and game rules into one large HTML document.

## Instructions for coding agents

Put project instructions in an `AGENTS.md` at the game repository root. Include the engine, build and test commands, module responsibilities, asset licensing and the supported SDK version. Link to the current service documentation rather than asking an agent to guess endpoint names.

Ask generated changes to handle signed-out, offline, quota and version-conflict states. Review code and dependencies before a release, regardless of how the code was produced.

## Authority and secrets

The browser is controlled by the player. A browser-reported score or save file cannot authorize a monetary reward. Put authoritative multiplayer rules and any sensitive validation on a trusted server.

Database passwords, OAuth secrets, GitHub access tokens and signing keys must not appear in frontend code or build artifacts. An environment variable compiled into browser code is public, even if its name includes “secret.”

## External services

You can design your game around your own backend or database. The future platform integration must still use scoped authorization for Spawn services. A shared account does not grant a game unrestricted access to a player's profile or to other games' data.
