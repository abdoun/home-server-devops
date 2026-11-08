# Services Documentation

This document describes the applications currently running on the home server.

## 1. CasaOS

**Purpose:** Web-based server management.

- Used to manage Docker applications.
- Main management interface for the server.

## 2. Nextcloud

**Purpose:** Self-hosted cloud storage and file management.

- Runs in Docker.
- Uses MariaDB as its database.
- Accessible through the home LAN and Tailscale.

## 3. Jellyfin

**Purpose:** Self-hosted media server.

- Runs in Docker.
- Provides media streaming on the private network.
- Uses TCP ports 8096 and 8920.

## 4. Syncthing

**Purpose:** File synchronization between devices.

- Runs in Docker.
- Uses TCP ports 8384 and 22000.
- Uses UDP ports 21027 and 22000.

## 5. SearXNG

**Purpose:** Self-hosted metasearch engine.

- Runs in Docker.
- Published on TCP port 8888.
- Accessible through the private network.

## 6. DailyExpense

**Purpose:** Personal expense management application.

- Laravel application.
- Uses MariaDB.
- Bound to localhost on port 18081.

## 7. Tunnel Test

**Purpose:** Testing reverse proxy and tunnel configurations.

- Uses an Nginx container.
- Bound to localhost on port 18080.

## 8. Nur Hub

**Purpose:** Python-based application.

- Runs with host networking.
- Application listens on TCP port 8770.

## 9. Cloudflared

**Purpose:** Cloudflare Tunnel client.

- Installed on the host.
- Tunnel configuration and production deployment are still pending.

---

## Notes

- Do not publish private credentials or `.env` files.
- Review port exposure before adding new services.
- Keep private applications behind LAN or Tailscale access controls.