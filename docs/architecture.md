# DeskSoul Architecture

## Overview

DeskSoul is an AI desktop pet application built with a modular architecture.

Core layers:

- Desktop App (Electron + Vue)
- Pet Core (state machine + behavior)
- Renderer (Live2D / VRM)
- Brain Core (AI abstraction)
- External AI (AstrBot / OpenAI-compatible)

## High-level Design

```text
User Interaction
    ↓
Pet Core (state + emotion + motion)
    ↓
Renderer (Live2D / VRM)
    ↓
Desktop UI (Electron windows)

Pet Core ↔ Brain Core ↔ AI Provider
```

## Modules

### 1. Pet Core

Handles:
- state machine
- emotion
- motion
- interaction events

### 2. Renderer

Adapters:
- Live2D (MVP)
- VRM (later)

### 3. Brain Core

Abstracts AI providers:
- OpenAI-compatible
- AstrBot (future)

### 4. Desktop Layer

Electron handles:
- windows
- tray
- system integration

## Design Principles

- Decoupled modules
- Replaceable AI providers
- Renderer abstraction
- Platform-first (Windows)
- Non-commercial asset safety
