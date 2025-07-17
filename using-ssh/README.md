# Deployment Guide

## Key Notes
- **rsync** is recommended over FTP for deployment because:
  - It's faster
  - Supports delta transfers (only sends changed parts of files)
  - Can exclude unnecessary files

## Excluded Files
The following files/directories are excluded from deployment:
- `.env` (to avoid overwriting configuration)
- `storage/` (to preserve logs, sessions, and other runtime files)

## Composer Flags
When installing dependencies in production:
```bash
composer install --no-dev --optimize-autoloader

## Install rsync
Ubuntu/Debian
```bash
sudo apt update -y      # Update packages
sudo apt install -y rsync