# Backup and Recovery

## 1. Current Backup Status

A dedicated backup system has not yet been configured.

Current storage:

| Component | Details |
|---|---|
| Main disk | 465.8 GB HDD |
| Partition | `/dev/sda1` |
| Filesystem | ext4 |
| Available space | Approximately 413 GB at last inspection |
| Separate backup disk | Not detected |

## 2. Backup Strategy

The planned backup strategy is to use separate physical storage.

Important data to protect includes:

- Nextcloud files and database.
- Application databases.
- Docker Compose files.
- Application configuration files.
- Important server configuration.

## 3. Recovery Planning

Recovery procedures have not yet been implemented or tested.

The planned recovery process includes:

1. Prepare a replacement storage device or server.
2. Restore application configuration files.
3. Restore application data and database backups.
4. Redeploy Docker Compose applications.
5. Verify application functionality.

## 4. Pending Tasks

- [ ] Obtain dedicated backup storage.
- [ ] Define backup schedules.
- [ ] Configure automated backups.
- [ ] Keep database backups consistent.
- [ ] Store copies of important configuration files.
- [ ] Test restoring Nextcloud.
- [ ] Test restoring application databases.
- [ ] Document the complete recovery procedure.

## 5. Security Notes

- Keep backup storage separate from the main server disk.
- Protect backups containing personal data.
- Never commit database dumps, credentials, or private configuration files to GitHub.
- Verify that backups can actually be restored.