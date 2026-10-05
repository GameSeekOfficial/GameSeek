# API reference

GameSeek clients talk to the backend with JSON WebSocket messages and a small set of HTTP routes.

The production host used by these endpoints is `https://gameseekapp.xyz`. Local development uses `http://localhost:8080`. The public product site is [gameseekapp.com](https://gameseekapp.com).

## WebSocket events

Every message is a JSON object with a `type` field.

### Client to server

| Type | Purpose |
| --- | --- |
| `send_message` | Send a chat message |
| `edit_message` | Edit a message |
| `delete_message` | Delete a message |
| `join_channel` | Join a text or voice channel |
| `leave_channel` | Leave a channel |
| `webrtc_offer` | Send a WebRTC offer for voice or screen share |
| `webrtc_answer` | Send a WebRTC answer |
| `webrtc_ice` | Send an ICE candidate |

### Server to client

| Type | Purpose |
| --- | --- |
| `message` | Broadcast a new chat message |
| `message_edited` | Broadcast an edit |
| `message_deleted` | Broadcast a deletion |
| `user_joined` | Someone joined the channel |
| `user_left` | Someone left the channel |
| `webrtc_offer` | Forwarded WebRTC offer |
| `webrtc_answer` | Forwarded WebRTC answer |
| `webrtc_ice` | Forwarded ICE candidate |

Browsers connect at `wss://gameseekapp.xyz/ws`. The Electron app connects at `ws://gameseekapp.xyz:8765`. See [Deployment](deployment.md) for the proxy.

## HTTP endpoints

### Accounts

| Method | Path | Purpose |
| --- | --- | --- |
| `POST` | `/register` | Register a user |
| `POST` | `/verify-email` | Confirm a 6-digit code |
| `POST` | `/login` | Start login |
| `POST` | `/login-verify` | Confirm the login code |

### Support

| Method | Path | Purpose |
| --- | --- | --- |
| `POST` | `/support` | Submit a support ticket |

Example body:

```json
{
  "ticket_id": "GS-A1B2C3D4",
  "name": "Max Mustermann",
  "email": "user@example.com",
  "subject": "Login issue",
  "message": "I cannot log in to my account."
}
```

The client generates `ticket_id` in the form `GS-XXXXXXXX`.

How these calls fit the rest of the system is described in [Architecture](architecture.md).
