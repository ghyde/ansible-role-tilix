# tilix

[Tilix][tilix] is an advanced GTK3 tiling terminal emulator that follows the
GNOME Human Interface Guidelines. This Ansible role installs and configures
Tilix on Fedora.

## Role Variables

### defaults/main.yml

|name|description|type|default|
|---|---|---|---|
|tilix_preferences_backup_file|Path to backup file of Tilix preferences|file path|/tmp/tilix_preferences.{{ ansible_date_time.epoch }}|
|tilix_install_dropdown_extension|Install [TilixDropdown][tilixdropdown] extension?|bool|True|

### vars/main.yml

|name|description|type|default|
|---|---|---|---|
|tilix_dropdown_extension_name|Name of [TilixDropdown][tilixdropdown] in the GNOME Shell extensions directory|string|TilixDropdown@ivkuzev@gmail.com|

## Example Playbook

```yaml
- hosts: workstations
  tasks:
  - import_role:
      name: libvirt
    vars:
      tilix_install_dropdown_extension: True
```

## Post-Install Requirements

You will need to restart GNOME Shell in order for the extension
[TilixDropdown][tilixdropdown] to become active. On Fedora running Wayland,
this requires logging out and logging back in.

## License

[MIT](LICENSE)


[tilix]: https://gnunn1.github.io/tilix-web/
[tilixdropdown]: https://github.com/ivoarch/gnome-shell-TilixDropdown
