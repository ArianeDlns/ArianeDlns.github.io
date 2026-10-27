---
title: "Harness engineering for an agent-built music player"
excerpt: "<br/>A NAS backend and an iOS client, written with coding agents. The harness is the contract, the invariants, and the checks that enforce them.<br><img src='/images/portfolio/music-player-architecture.svg' width='100%' alt='Architecture of the music player: Synology NAS, iPhone app, and Mac, connected over Tailscale.'>"
collection: portfolio
date: 2026-08-30
redirect_from:
  - /publications/2026-08-31-harness-engineering-music-player/
---

A personal music player, split across two repositories: [music-player-backend](https://github.com/ArianeDlns/music-player-backend), a FastAPI service on a Synology NAS, and [MusicPlayer-Client](https://github.com/ArianeDlns/MusicPlayer-Client), a SwiftUI app. They never share a process. They meet on an HTTP contract. Both were written with coding agents.

The harness is what keeps that arrangement from drifting.

**One contract, two sessions.** `docs/contract-v1.md` describes the API that is actually deployed. It lists the routes that exist (`/health`, `/catalog/delta`, `/file`, `/art`), the ones that are specified and still return 404, and how the delta-sync cursor has to move. A second agent can write the iOS client from that document alone. The architecture spec holds the intent. The contract holds the current truth, including the places where the two differ.

**Invariants, written down before the edit.** Each repository has a `CLAUDE.md` the agent reads first. On the backend, every catalog write increments `SyncVersion` in the same SQLite transaction, deletes are soft, the tag vocabulary is closed, and `match_key` stays frozen. On the client, the API token lives in the Keychain, audio files live in Application Support and are excluded from backup, and the sync cursor is written in the same GRDB transaction as the page it came from. A 401 is never retried.

**The same rules run outside the prompt.** The backend runs ruff, strict mypy, and pytest. Pre-commit and GitHub Actions pin the same ruff version, so a change that passes locally also passes on push. The iOS repository adds a hook that runs after each Swift edit and flags a hardcoded token, audio stored under Caches, a global ATS exception, or a retry on 401. The agent's shell may run the build tools. It may not run `rm -rf` or a force-push.

The catalog foundation is implemented and tested: indexing, soft delete, delta sync, ranged file delivery, and cover art. Audio analysis, lyrics, and LLM tagging are in the schema and in the contract, and the code that fills them is not written yet. The harness says so, which stops the agent from inventing them.

<p align="center">
<img src="/images/portfolio/music-player-architecture.svg" width="100%" alt="Architecture of the music player: Synology NAS, iPhone app, and Mac, connected over Tailscale.">
</p>
