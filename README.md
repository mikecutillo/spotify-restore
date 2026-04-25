# Spotify Restore

A small Python utility that rebuilds a Spotify account's playlists and saved library after a loss event (account wipe, migration to a new account, accidental unfollow cascade) using the Spotify Web API.

> *This repo is a public overview. The running code is private.*

---

## What it is

If a Spotify account is accidentally emptied or a user migrates to a new one, Spotify itself doesn't offer a clean restore path. This utility reads a previously-exported library dump and recreates the state: liked songs, playlists (with original tracks in the original order), and followed artists.

## What it does

- **Authenticates via Spotify OAuth** with user-library-modify and playlist-modify scopes
- **Reads an export file** (JSON from a prior account) describing playlists, tracks, and saved albums
- **Rebuilds liked songs, playlists, and followed artists** in the correct order
- **Handles rate limits** — batches requests and respects Spotify's per-minute quotas
- **Idempotent** — re-running the same restore against a partially-rebuilt account won't duplicate work

## Software

| Layer | Tech |
|---|---|
| Script | Python |
| Auth | Spotify OAuth 2.0 |
| API | Spotify Web API |

## What this demonstrates

- **Minimal utility work** — a small, sharp tool that solves one specific problem
- **OAuth + rate-limit handling** — production realities on a consumer API
- **Idempotent restores** — re-runnable without fear

## Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Spotify](https://img.shields.io/badge/Spotify-1DB954?style=flat&logo=spotify&logoColor=white)

## Related in the AIOS Portfolio

- **[AIOS](https://github.com/mikecutillo/aios)** — Host pattern of OAuth + restore; Next.js dashboard orchestrating 16+ household and business modules
- **[AI Model Router](https://github.com/mikecutillo/ai-model-router)** — Kindred small-utility AIOS pattern; multi-provider LLM router with waterfall fallback

---

Part of the AIOS portfolio. See the [profile README](https://github.com/mikecutillo) for the full system map.
