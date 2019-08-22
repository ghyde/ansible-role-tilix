# tilix

[Tilix][tilix] is an advanced GTK3 tiling terminal emulator that follows the
GNOME Human Interface Guidelines. This Ansible role installs and configures
Tilix on Fedora.

## Role Variables

### defaults/main.yml

|name|description|type|default|
|---|---|---|---|
|tilix_preferences_backup_file|Path to backup file of Tilix preferences|file path|/tmp/tilix_preferences.{{ ansible_date_time.epoch }}|
|tilix_install_dropdown_extension|Install [TilixDropdown][tilix_dropdown] extension?|bool|False|

### vars/main.yml

|name|description|type|default|
|---|---|---|---|
|tilix_dropdown_extension_name|Name of [TilixDropdown][tilix_dropdown] in the GNOME Shell extensions directory|string|TilixDropdown@ivkuzev@gmail.com|
|tilix_dropdown_extension_src|URL to [TilixDropdown][tilix_dropdown] source code|URL|https://github.com/ivoarch/gnome-shell-TilixDropdown/archive/master.zip|

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
[TilixDropdown][tilix_dropdown] to become active. On Fedora running Wayland,
this requires logging out and logging back in.

## Update Preferences File

To update this role with your current Tilix preferences, run the following
command:

```bash
dconf dump /com/gexperts/Tilix/ > files/preferences
```

## License

[MIT](LICENSE)


[tilix]: https://gnunn1.github.io/tilix-web/
[tilix_dropdown]: https://github.com/ivoarch/gnome-shell-TilixDropdown
