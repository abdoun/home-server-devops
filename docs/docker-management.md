# Docker Management

## 1. Overview

Docker Engine is used to run and manage the containerized applications on the home server.

Docker Compose is used to define and manage multi-container applications.

## 2. Installed Components

| Component | Version / Details |
|---|---|
| Docker Engine | Installed |
| Docker Compose | 2.26.1-4 |
| Operating System | Debian GNU/Linux 13 |

## 3. Application Management

CasaOS provides a graphical interface for managing Docker applications.

Docker Compose projects can also be managed from the command line.

Common commands:

```bash
# List running containers
docker ps

# List all containers
docker ps -a

# Show Docker networks
docker network ls

# Show Docker volumes
docker volume ls

# View container logs
docker logs CONTAINER_NAME

# Follow container logs
docker logs -f CONTAINER_NAME

# Show Docker resource usage
docker stats
```

## 4. Docker Networking

The server uses:

- Default Docker bridge network.
- Custom bridge networks for selected applications.
- Host networking for Nur Hub.
- Localhost-only port bindings for selected applications.

## 5. Port Binding

Selected applications are bound to localhost:

| Application | Host Binding |
|---|---|
| DailyExpense | `127.0.0.1:18081` |
| Tunnel Test | `127.0.0.1:18080` |

Other services use published Docker ports and are subject to firewall restrictions.

## 6. Security Considerations

- Avoid exposing container management interfaces publicly.
- Review published ports before deploying new containers.
- Keep credentials in environment files outside Git.
- Do not commit database credentials or secrets.
- Review Docker firewall rules after changing container networking.

## 7. Pending Improvements

- [ ] Organize Compose files and deployment directories.
- [ ] Document container volumes and persistent data locations.
- [ ] Persist Docker firewall rules.
- [ ] Add container health monitoring.
- [ ] Document backup and recovery procedures.