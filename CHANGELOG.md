# Changelog

## 0.0.2

- Fix `automatic_upgrade` and `automatic_clean` defaults from `"true"` to `1` — `apt.systemd.daily` requires numeric intervals, not boolean strings

## 0.0.1 – 2026-06-13

- Initial release
- Install and configure `unattended-upgrades` for automatic security patches
- Install `needrestart` for restart notification/automation
- Configurable origins, blacklist, auto-reboot, email reports
- Template-driven `/etc/apt/apt.conf.d/20auto-upgrades` and `50unattended-upgrades`
