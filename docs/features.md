# ✨ Features

An overview of all major features in GameSeek.

-----

## 💬 Messaging

- Real-time text chat via WebSocket
- Edit & delete messages (right-click context menu)
- Live broadcast of edits/deletes to all connected users
- Auto-scroll to latest message

-----

## 🎤 Voice & Video

- Voice channels with WebRTC peer-to-peer audio
- Screen sharing with multi-stream grid layout
- Background noise suppression
- Speaking indicator (no flicker)
- WebRTC renegotiation for mid-session stream changes

-----

## 🖥️ Desktop App (Electron)

- Native Windows desktop application
- Windows push notifications via Electron IPC
- Connects directly to backend via `ws://` (no proxy needed)
- Auto-detects EXE vs browser environment

-----

## 🌐 Web App

- Full browser support
- Connects via `wss://` through Nginx reverse proxy
- Same feature parity as the desktop app

-----

## 🛠️ Server Management

- Create and manage servers (like Discord guilds)
- Channel management (create, edit, delete)
- Role system with permissions
- Member management
- Server security settings
- Danger zone (delete server, transfer ownership)

-----

## 👤 Accounts & Auth

- User registration with 6-digit email verification
- Login with email verification code
- Profile management

-----

## 🎫 Support System

- Support ticket submission from the website
- Tickets assigned unique `GS-XXXXXXXX` IDs
- Email delivery via SendGrid
- Support page available in 🇩🇪 German and 🇬🇧 English

-----

## 📊 Admin Tools

- Admin dashboard for platform management
- User oversight and moderation tools

-----

> More features are actively being developed. See [CHANGELOGS](../CHANGELOGS/) for the latest updates.
