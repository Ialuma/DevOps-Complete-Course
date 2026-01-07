# DevOps Troubleshooting: Git & SSH
This document records the fixes for authentication and permission issues encountered during setup.

## SSH Key Management
- **Issue**: System not recognizing keys or "Permission Denied (publickey)".
- **Fix**: 
  - Ensure keys are in `~/.ssh/` of the current user, not root.
  - Verify connection with: `ssh -T git@github.com`

## Linux Permissions
- **SSH Folder**: Must be `700` (drwx------).
- **Private Key**: Must be `600` (-rw-------).
- **Ownership**: Use `sudo chown -R $USER:$USER <path>` to reclaim files from root.

## Git Remote Configuration
- Always use the SSH URL (`git@github.com:...`) to avoid Personal Access Token prompts.
- Switch URL: `git remote set-url origin <SSH_URL>`
