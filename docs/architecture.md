# Architecture

GameSeek is a realtime communication platform with three runtime pieces: a Windows app, a web app, and a Python backend.

This repository documents the project. It does not contain the application source.

## Tech stack

| Layer | Technology |
| --- | --- |
| Desktop app | Electron |
| Frontend | React and TypeScript |
| Backend | Python (asyncio) |
| Realtime messaging | WebSockets |
| Voice and video | WebRTC |
| Database | SQLite |
| Server | Debian |
| Reverse proxy | Nginx |
| Email | SendGrid |

## Shape of the system

```text
Client
├── Electron app ── ws://host:8765 ──────────────┐
└── Browser ────── wss://host/ws (Nginx) ────────┤
                                                 ▼
                                    Python backend
                                    ├── WebSocket server :8765
                                    ├── HTTP server      :8080
                                    └── SQLite
```

## Decisions that matter

### Electron and the browser

The frontend checks its environment at startup:

```typescript
const isElectron = !!(window as any).require;
```

That flag selects the WebSocket URL and turns on platform features such as native Windows notifications.

### Voice and screen share

- Media is peer to peer over WebRTC.
- The Python backend only signals the call. It does not relay audio or video.
- Noise suppression uses browser APIs.
- Speaking detection uses `setInterval` and `useRef`, which avoids a flickering audio stream.

### Messages

Chat sends, edits, and deletes are broadcast on the WebSocket. A right-click menu edits or deletes a message in place, and every connected client sees the change.

### Email and support

- Support ticket IDs look like `GS-XXXXXXXX`.
- Mail is sent with SendGrid from `support@gameseekapp.xyz`.
- Register and login use a 6-digit email code.

The public website is [gameseekapp.com](https://gameseekapp.com). The host named in deployment and API docs is `gameseekapp.xyz`.

## Where the code is expected to live

```text
frontend/          Electron and React app
└── src/
    ├── components/
    └── pages/
backend/           Python WebSocket and HTTP server
```

## Where the docs live

```text
README.md
CHANGELOG.md
CONTRIBUTING.md
CODE_OF_CONDUCT.md
SECURITY.md
docs/
├── getting-started.md
├── features.md
├── architecture.md
├── api.md
├── deployment.md
├── security/
└── legal/
assets/screenshots/
brand/
```

Event and route names are listed in the [API reference](api.md).
