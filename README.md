# Hestia Init

## Usage Overview

You will run **Phase One**, reboot, then run **Phase Two**, and reboot again.

- Phase One -> reboot
- Phase Two -> reboot

## Run Phase One

> **Run this as root.**

```bash
curl -fsSL https://raw.githubusercontent.com/RSKYS/Hestia--init/master/phase-one | bash
```

### Phase One Prompts

- `USER`: Existing Hestia admin username.
- `DOMAIN`: New primary server domain (lowercase letters, digits, dots, hyphens).
- `WEB_MAIL_ALIAS`: Webmail prefix alias (letters, digits, hyphens).
- `PHP_ADMIN`: phpMyAdmin alias (letters, digits, hyphens).

### Phase One Actions

- Deletes all existing web domains for the given user.
- Updates hostname and system aliases in Hestia.
- Disables system backups.
- Restarts Hestia service.
- Prompts for a reboot (required).

## Run Phase Two

> **Run this as root (after reboot).**

```bash
curl -fsSL https://raw.githubusercontent.com/RSKYS/Hestia--init/master/phase-two | bash
```

### Phase Two Prompts

- `USER`: Existing Hestia admin username.
- `DOMAIN`: Primary server domain.
- `WEB_MAIL_ALIAS`: Webmail prefix alias.

### Phase Two Actions

- Adds the primary domain and enables Let’s Encrypt.
- Detects public IPv4 (or prompts for it).
- Creates `ns1` and `ns2` A records.
- Replaces the Hestia SSL cert with the domain cert.
- Rewrites Roundcube configuration for SSL/TLS settings.
- Restarts web/proxy/dns services.
- Prompts for a reboot (required).
