# Deployment

How the production host is set up.

## Server

| | |
| --- | --- |
| OS | Debian |
| Domain | gameseekapp.xyz |
| Reverse proxy | Nginx |
| TLS | Let's Encrypt |

The marketing site and product entry point are [gameseekapp.com](https://gameseekapp.com). This page describes the realtime host.

## WebSocket proxy

Two endpoints stay up at the same time.

| Endpoint | Client |
| --- | --- |
| `wss://gameseekapp.xyz/ws` | Browser |
| `ws://gameseekapp.xyz:8765` | Electron app |

Nginx proxies the browser path to the local WebSocket server:

```nginx
location /ws {
    proxy_pass http://localhost:8765;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "Upgrade";
    proxy_set_header Host $host;
}
```

## TLS

Certificates come from Nginx and Let's Encrypt (`certbot`):

```bash
certbot --nginx -d gameseekapp.xyz -d www.gameseekapp.xyz
```

## Email

SendGrid sends support mail.

- The domain is authenticated with CNAME records at Porkbun.
- An SPF record is set for `gameseekapp.xyz`.
- `FROM_EMAIL` is `support@gameseekapp.xyz`.

## Process

Start the backend from the backend directory:

```bash
cd backend
nohup python server.py &
```

`systemd` or `pm2` is a better fit when the process should restart on its own.

Ship an update with:

```bash
git pull origin main
pkill -f server.py
nohup python server.py &
cd frontend && npm run build
```

Related: [Architecture](architecture.md) · [API](api.md)
