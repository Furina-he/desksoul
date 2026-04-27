# ADR-0000: DeskSoul Project Decisions

Date: 2026-04-27

## Decisions

1. Project codename: DeskSoul.
2. Main route: AIRI-inspired desktop companion architecture.
3. AstrBot integration: external service only, not bundled in MVP.
4. Mate-Engine usage: behavior reference only, no source or asset merging.
5. Character rendering: Live2D first, VRM second.
6. Platform priority: Windows first, macOS/Linux later.
7. Code license: AGPL-3.0-or-later.
8. Asset license: CC BY-NC-SA 4.0.
9. Repository style: new independent repository.
10. AIRI reuse: selective MIT code reuse with attribution.
11. Default assets: placeholder only in early versions.

## Rationale

These decisions aim to balance:
- development speed
- legal safety (especially around assets)
- extensibility
- community contribution friendliness

The architecture intentionally decouples:
- rendering (Live2D / VRM)
- AI providers (OpenAI-compatible / AstrBot)
- desktop behaviors

so the system can evolve without large refactors.
