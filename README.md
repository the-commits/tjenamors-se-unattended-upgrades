[![sourcehut](https://img.shields.io/badge/sourcehut-~the--commits/tjenamors--se--unattended--upgrades-2d6b9e?logo=sourcehut)](https://git.sr.ht/~the-commits/tjenamors-se-unattended-upgrades)
[![GitHub mirror](https://img.shields.io/badge/GitHub-the--commits/tjenamors--se--unattended--upgrades-181717?logo=github)](https://github.com/the-commits/tjenamors-se-unattended-upgrades)

# Unattended Upgrades

Configure `unattended-upgrades` for automatic security patching on Debian/Ubuntu, with `needrestart` for restart handling.

## Features

- **Security-only by default** — only packages from `-security` origins are auto-upgraded
- **Configurable origins** — extend to `-updates` or custom repos as needed
- **Package blacklist** — prevent specific packages from being auto-upgraded
- **Auto-reboot** — optional scheduled reboot when a kernel update requires it
- **Email reports** — optional mail notifications on upgrade results
- **Needrestart** — automatic restart of services after library upgrades
- **Idempotent** — safe to re-run

## Requirements

- Ansible 2.14+
- Root/sudo access on target hosts
- Debian or Ubuntu target

## Role Variables

| Variable | Default | Description |
|---|---|---|
| `unattended_upgrades_install` | `true` | Install and configure packages |
| `unattended_upgrades_packages` | `[unattended-upgrades, needrestart]` | Packages to install |
| `unattended_upgrades_update_days` | `0` | APT update interval (days, 0 = every timer fire) |
| `unattended_upgrades_automatic_upgrade` | `"true"` | Automatically download & install upgrades |
| `unattended_upgrades_automatic_clean` | `"true"` | Auto-clean downloaded archives |
| `unattended_upgrades_origins` | `["${distro_id}:${distro_codename}-security", ...]` | Package origins to auto-upgrade |
| `unattended_upgrades_package_blacklist` | `[]` | Packages to never auto-upgrade |
| `unattended_upgrades_automatic_reboot` | `false` | Reboot automatically after kernel upgrade |
| `unattended_upgrades_automatic_reboot_time` | `"02:00"` | Scheduled reboot time |
| `unattended_upgrades_email_from` | `"root"` | Email sender address |
| `unattended_upgrades_email_to` | `""` | Email recipient (empty = no mail) |
| `unattended_upgrades_email_only_on_error` | `true` | Only send mail on errors |
| `unattended_upgrades_needrestart_mode` | `"a"` | Needrestart restart mode (`a` = auto, `i` = interactive) |

## Example Playbook

```yaml
- hosts: all
  become: true
  vars:
    unattended_upgrades_automatic_reboot: true
    unattended_upgrades_automatic_reboot_time: "03:00"
    unattended_upgrades_email_to: "admin@example.com"
  roles:
    - role: unattended_upgrades
```

## License

AGPL-3.0 — see [LICENSE](LICENSE) for details.
