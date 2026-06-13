# Changelog

## 0.0.2 – 2026-06-13

- Add playbook wiring instructions to AGENTS.md
- Wire role into tjenamors-se-ansible hardening play

## 0.0.1 – 2026-06-13

- Initial release
- Install and configure `unattended-upgrades` for automatic security patches
- Install `needrestart` for restart notification/automation
- Configurable origins, blacklist, auto-reboot, email reports
- Template-driven `/etc/apt/apt.conf.d/20auto-upgrades` and `50unattended-upgrades`
