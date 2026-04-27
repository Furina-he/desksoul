# DeskSoul

DeskSoul is a non-commercial open-source AI desktop pet application.

It aims to provide a cute, interactive AI companion on your desktop with:

- Live2D-first character rendering, with VRM planned later
- Text chat in the MVP
- Voice interaction in later versions
- Emotion and motion reactions
- Optional AstrBot integration as an external AI brain
- Mate-like desktop pet behaviors implemented from scratch

> Status: early planning and foundation stage. Not ready for daily use yet.

## Goals

- Build a lightweight AI desktop pet for Windows first.
- Support character packs.
- Support external AI brains such as AstrBot.
- Provide a plugin-friendly architecture.
- Keep the project community-oriented and non-commercial.

## Non-goals

- Commercial distribution of the official project build.
- Bundling copyrighted character models without permission.
- Copying Mate-Engine source code or assets into the main repository.
- Replacing AstrBot.
- Building a general-purpose automation agent in the MVP.

## Architecture

DeskSoul is planned as an independent repository inspired by AIRI's desktop companion direction:

```text
DeskSoul Desktop App
  Electron + Vue + TypeScript
  ├─ Pet Core: state machine, emotion, motion, event bus
  ├─ Renderer: Live2D first, VRM later
  ├─ Brain Core: provider abstraction
  ├─ Brain Providers: OpenAI-compatible first, AstrBot bridge later
  ├─ Voice Core: STT / TTS later
  └─ Desktop Behavior: drag, click, sleep, edge snap, window sit later
```

AstrBot will be integrated as an external service through its HTTP API. DeskSoul will not bundle AstrBot in the MVP.

Mate-Engine is used only as interaction design reference. This repository does not copy or bundle Mate-Engine source code or assets.

## Roadmap

- v0.0: Project foundation
- v0.1: Desktop pet + text chat
- v0.2: Voice + emotion + motion
- v0.3: AstrBot Bridge
- v0.4: Mate-like desktop behaviors
- v0.5: Character packs and plugin SDK

See [docs/roadmap.md](docs/roadmap.md) for details.

## Development

Planned setup:

```bash
pnpm install
pnpm dev:desktop
```

The runnable Electron app scaffold will be added in the first development milestone.

## License

- Code: AGPL-3.0-or-later
- Original DeskSoul assets: CC BY-NC-SA 4.0 unless otherwise stated

See [LICENSE](LICENSE), [ASSETS_LICENSE.md](ASSETS_LICENSE.md), [NOTICE](NOTICE), and [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
