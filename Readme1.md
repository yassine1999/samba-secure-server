# Secure Samba File Server (Ubuntu + Windows)

This project sets up a secure file server using **Samba** on Ubuntu, allowing authenticated file sharing between Linux and Windows systems.

## 🔐 Features

- Password-protected access with Samba user management
- Group-based access control (e.g., `securegroup`)
- Enforced secure protocols (SMB2/3)
- Audit logging with `vfs_full_audit`
- Tested with Windows 10/11

## 📁 Share Configuration

```ini
[SecureShare]
   path = /srv/samba/secure-share
   valid users = yassine
   guest ok = no
   read only = no
   create mask = 0770
   directory mask = 0770
  ; vfs objects = full_audit
   full_audit:prefix = %u|%I|%m|%S
   full_audit:success = read,write,rename
   full_audit:failure = none
   full_audit:facility = LOCAL7
   full_audit:priority = NOTICE
