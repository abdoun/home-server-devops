# Home Server & DevOps

Personal home server infrastructure and DevOps documentation.

This repository documents the architecture, configuration, services, networking, security, and ongoing improvements of my home server.

## 1. Hardware

| Component | Specification |
|---|---|
| Device | Laptop |
| CPU | Intel Core i3-3217U |
| RAM | 8 GB |
| Storage | 465.8 GB HDD |
| Operating System | Debian GNU/Linux 13 |
| Filesystem | ext4 |

## 2. Infrastructure

- Debian 13 (Trixie)
- CasaOS
- Docker Engine
- Docker Compose
- UFW Firewall
- iptables
- Tailscale VPN
- Cloudflared (installed)

## 3. Running Services

| Service | Purpose | Access |
|---|---|---|
| CasaOS | Server management | LAN |
| Nextcloud | Private cloud storage | LAN / Tailscale |
| Jellyfin | Media server | LAN / Tailscale |
| Syncthing | File synchronization | LAN / Tailscale |
| SearXNG | Private metasearch | LAN / Tailscale |
| DailyExpense | Laravel application | Localhost |
| Tunnel Test | Nginx test service | Localhost |
| Nur Hub | Python application | Host network |

## 4. Networking

### Remote Access
- Tailscale installed and operational.
- MagicDNS enabled.
- Server accessible remotely through the tailnet.
- SSH access available through Tailscale.

### Docker Networking
- Multiple Docker bridge networks.
- Docker-published services are configured for restricted access.
- Localhost-only bindings used for selected applications.

## 5. Firewall & Security

- UFW enabled.
- Default incoming policy: DENY.
- Default outgoing policy: ALLOW.
- Routed traffic policy: DENY.
- SSH restricted to LAN and Tailscale.
- Docker `DOCKER-USER` rules configured for selected published ports.
- IPv6 forwarding disabled.
- IPv6 incoming traffic blocked by default.

**Pending:**
- Verify external IPv4 and IPv6 access restrictions.
- Persist Docker firewall rules across reboots.
- Verify firewall behavior after reboot.

## 6. Power Management

The server is configured to remain operational when the laptop lid is closed.

Configuration file:

`/etc/systemd/logind.conf.d/lid-switch.conf`

```ini
[Login]
HandleLidSwitch=ignore
HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore
```

The configuration was reloaded and tested successfully.

## 7. Storage

- Main disk: approximately 450 GB.
- Filesystem: ext4.
- Available space at last inspection: approximately 413 GB.
- No dedicated backup disk currently available.

**Backup system: Not yet configured.**

## 8. Current Roadmap

- [x] Install Debian and CasaOS.
- [x] Install and configure Docker.
- [x] Deploy core services.
- [x] Configure Tailscale remote access.
- [x] Configure UFW.
- [x] Configure Docker firewall restrictions.
- [x] Add Nextcloud Tailscale address to trusted domains.
- [x] Configure laptop lid behavior.
- [ ] Verify external firewall protection.
- [ ] Persist firewall rules.
- [ ] Set up automated backups.
- [ ] Test backup restoration.
- [ ] Set up server monitoring and alerts.
- [ ] Improve project deployment organization.
- [ ] Configure Cloudflare Tunnel with a domain.

## 9. Security Notes

- Never commit passwords, API tokens, SSH private keys, or database credentials.
- Keep sensitive configuration files outside Git.
- Review firewall rules before exposing new services.
- Prefer Tailscale for private remote access.
- Maintain backups on separate physical storage.

## 10. Documentation

Detailed documentation is maintained in the `docs/` directory.

---

**Project status:** Active development

**Last documented milestone:** November 2026