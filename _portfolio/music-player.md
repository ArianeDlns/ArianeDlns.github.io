---
title: "Harness engineering for an agent-built music player"
excerpt: "<br/>Personal music stack written with coding agents: a FastAPI service on a Synology NAS and a SwiftUI iOS client, held together by a contract and checks the agent cannot skip.<br><img src='/images/portfolio/music-player-architecture.svg' width='100%' alt='Architecture of the music player: Synology NAS, iPhone app, and Mac, connected over Tailscale.'>"
collection: portfolio
date: 2026-08-30
redirect_from:
  - /publications/2026-08-31-harness-engineering-music-player/
---

Personal music player in two repositories: [music-player-backend](https://github.com/ArianeDlns/music-player-backend) and [MusicPlayer-Client](https://github.com/ArianeDlns/MusicPlayer-Client). I designed the harness, then used coding agents to implement it. The NAS is the catalog. The iPhone is an offline mirror. They only meet over HTTP, on Tailscale.

<p align="center">
<img src="/images/portfolio/music-player-architecture.svg" width="100%" alt="Architecture of the music player: Synology NAS, iPhone app, and Mac, connected over Tailscale.">
</p>

**What this shows**

* **Harness design.** Each repository has a `CLAUDE.md` the agent reads before editing. Invariants are explicit: `SyncVersion` moves in the same SQLite transaction as the catalog write, deletes are soft, the tag vocabulary is closed, the API token stays in the Keychain, and audio files stay in Application Support.
* **Contract-first split.** `docs/contract-v1.md` is the deployed API, including the routes that still return 404. A second agent can build the iOS client from that document. The architecture spec stays the intent. The contract stays the current truth.
* **Checks outside the prompt.** Backend: ruff, strict mypy, and pytest, with the same ruff version in pre-commit and GitHub Actions. iOS: a hook after each Swift edit that flags a hardcoded token, audio under Caches, a global ATS exception, or a retry on 401.
* **Stack.** Python 3.12, FastAPI, SQLite WAL, Docker on a Synology DS920+. Swift, SwiftUI, GRDB, AVAudioEngine.

Built and tested: indexing, soft delete, delta sync, ranged audio delivery, cover art. Audio analysis, lyrics, and LLM tagging are specified in the contract and not implemented yet.
