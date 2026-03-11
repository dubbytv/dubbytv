<h1 align="center"><strong>dubby</strong></h1>

<p align="center">
  <strong>Self-hosted streaming, built with care.</strong>
</p>

<p align="center">
  A modern media server with reliable playback, clean design, and respect for your privacy.<br>
  No ads. No hardware tax. Free for local use.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-In_Active_Development-0ea5e9?style=flat-square" alt="In Active Development">
  &nbsp;
  <a href="https://dubby.tv"><img src="https://img.shields.io/badge/website-dubby.tv-0ea5e9?style=flat-square" alt="dubby.tv"></a>
</p>

<p align="center">
  <img src="screenshots/home.png" alt="dubby — home screen with continue watching and library stats" width="720">
</p>

---

## What dubby gets right

- **Plays Everything** — Seven playback tiers from direct play to full transcode. dubby always finds a working mode — no "format not supported" screens, ever.

- **HDR & Dolby Vision** — HDR10, Dolby Vision, HLG passthrough with automatic tone-mapping fallback. TrueHD and Atmos audio pass straight through.

- **Skip Intro & Credits** — Audio fingerprinting detects intros across episodes automatically. One tap to skip — no subscription required.

- **Seek Preview Thumbnails** — Scrub through any file and see exactly where you are. Trickplay sprites generated automatically — free, not behind a paywall.

- **Native TV Apps** — Apple TV and Android TV apps built with native playback engines, D-pad navigation, and full HDR support. Not a web wrapper.

- **GPU Transcoding, No Paywall** — Intel QSV, NVIDIA NVENC, AMD VAAPI, Apple VideoToolbox. Full hardware acceleration included for every user.

- **Discover & Request** — Browse trending content and request new movies or shows directly from the app. Built-in Seerr integration — no extra setup.

- **Smart Metadata** — TMDB, TVDB, Trakt, and MDBList enrichment. Artwork, cast, ratings, and subtitles fetched and organized automatically.

- **Ahead-of-Time Optimization** — Pre-transcode your library for instant playback on any device. A smart coverage matrix builds the minimum set of variants needed.

- **Backup & Restore** — Scheduled backups with retention policies. Download archives, upload to a new server, restore with one click.

- **Multi-User Profiles** — Separate watch progress, language preferences, and library permissions per user. Invite-only registration with role-based access.

- **Private by Default** — No ads. No data selling. No cloud account required. Telemetry is opt-out and transparent. Your server, your rules.

<p align="center">
  <img src="screenshots/movies.png" alt="dubby — movie library" width="720">
</p>

---

## Screenshots

<p align="center">
  <img src="screenshots/yellowstone.png" alt="dubby — TV show detail" width="720">
</p>

<p align="center">
  <img src="screenshots/F1.png" alt="dubby — movie detail with Dolby Vision badge and ratings" width="720">
</p>

<p align="center">
  <img src="screenshots/discover.png" alt="dubby — discover and request" width="720">
</p>

<p align="center">
  <img src="screenshots/dashboard.png" alt="dubby — admin dashboard" width="720">
</p>

---

## Quick Start

```yaml
services:
  dubby:
    image: dubbytv/dubby:stable
    ports:
      - "3000:3000"
    environment:
      - BETTER_AUTH_SECRET=${BETTER_AUTH_SECRET:?Set BETTER_AUTH_SECRET in .env}
      - TMDB_API_KEY=${TMDB_API_KEY:-}
      - REDIS_URL=redis://valkey:6379
    volumes:
      - dubby-data:/data
      - dubby-cache:/cache
      - /path/to/media:/media:ro
    depends_on:
      valkey:
        condition: service_healthy

  valkey:
    image: valkey/valkey:latest
    volumes:
      - valkey-data:/data
    healthcheck:
      test: ['CMD', 'valkey-cli', 'ping']
      interval: 10s
      timeout: 5s
      retries: 3

volumes:
  dubby-data:
  dubby-cache:
  valkey-data:
```

```bash
# Generate a secret
echo "BETTER_AUTH_SECRET=$(openssl rand -base64 32)" > .env

# Start
docker compose up -d

# Open http://localhost:3000
```

---

## How dubby compares

|  | dubby | Plex | Emby | Jellyfin |
|---|:---:|:---:|:---:|:---:|
| **Philosophy** | | | | |
| Free for local use | :white_check_mark: | :white_check_mark: | :heavy_minus_sign: | :white_check_mark: |
| No ads or tracking | :white_check_mark: | :x: | :heavy_minus_sign: | :white_check_mark: |
| Privacy by default | :white_check_mark: | :x: | :heavy_minus_sign: | :white_check_mark: |
| Modern, polished UI | :white_check_mark: | :heavy_minus_sign: | :x: | :x: |
| **Playback** | | | | |
| Adaptive playback engine | :white_check_mark: | :x: | :x: | :x: |
| HDR & Dolby Vision | :white_check_mark: | :heavy_minus_sign: | :heavy_minus_sign: | :heavy_minus_sign: |
| HDR tone-mapping (free) | :white_check_mark: | :x: | :x: | :white_check_mark: |
| HW transcoding included | :white_check_mark: | :x: | :x: | :white_check_mark: |
| Trickplay previews (free) | :white_check_mark: | :x: | :x: | :white_check_mark: |
| Skip intro (free) | :white_check_mark: | :x: | :x: | :heavy_minus_sign: |
| **Platform** | | | | |
| Native TV apps | :white_check_mark: | :white_check_mark: | :white_check_mark: | :heavy_minus_sign: |
| **Features** | | | | |
| Media requests built-in | :white_check_mark: | :x: | :x: | :x: |
| Ahead-of-time optimization | :white_check_mark: | :heavy_minus_sign: | :x: | :x: |
| Backup & restore | :white_check_mark: | :x: | :heavy_minus_sign: | :x: |
| Prometheus monitoring | :white_check_mark: | :x: | :x: | :x: |

<sub>Comparison accurate as of March 2026. Features may change as all projects evolve.</sub>

---

## Supported Platforms

| Architecture | Available |
|---|:---:|
| x86-64 (amd64) | :white_check_mark: |
| arm64 (Apple Silicon, RPi) | :white_check_mark: |

---

## Links

- **Website** — [dubby.tv](https://dubby.tv)
- **Newsletter** — [Weekly dev updates](https://dubby.tv/#newsletter)
- **Contact** — [woof@dubby.tv](mailto:woof@dubby.tv)
