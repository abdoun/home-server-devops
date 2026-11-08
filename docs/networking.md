# Networking Documentation

## 1. Overview

The home server uses a combination of local networking, Docker networking, and Tailscale for private remote access.

## 2. Network Interfaces

| Interface | Purpose |
|---|---|
| `enp1s0` | Physical LAN interface |
| `tailscale0` | Tailscale VPN interface |
| `docker0` | Default Docker bridge |
| `br-*` | Custom Docker bridge networks |

## 3. Remote Access

Tailscale provides private remote connectivity between authorized devices.

- MagicDNS is enabled.
- SSH access is available through Tailscale.
- No router port forwarding is required for Tailscale access.

## 4. Docker Networks

The server uses Docker bridge networks to isolate application containers.

| Network | Purpose |
|---|---|
| `docker0` | Default Docker bridge |
| Nextcloud bridge | Nextcloud application networking |
| Jellyfin bridge | Jellyfin application networking |
| DailyExpense bridge | DailyExpense application networking |
| Tunnel Test bridge | Tunnel Test application networking |

## 5. Published Ports

| Service | TCP Ports | UDP Ports |
|---|---|---|
| Jellyfin | 8096, 8920 | 1900, 7359 |
| Nextcloud | 10081, 10443 | — |
| Syncthing | 8384, 22000 | 21027, 22000 |
| SearXNG | 8888 | — |

DailyExpense and Tunnel Test are bound to localhost and are not intended for direct LAN access.

## 6. Firewall Design

### UFW

- Default incoming policy: DENY.
- Default outgoing policy: ALLOW.
- Default routed policy: DENY.
- SSH is allowed from the home LAN and Tailscale.

### Docker Firewall

Selected Docker-published ports are restricted using the `DOCKER-USER` chain.

The current rules are intended to permit access from:

- Home LAN: `192.168.178.0/24`
- Tailscale interface