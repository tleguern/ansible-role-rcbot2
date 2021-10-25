# Ansible Role: Day of Defeat: Source RCBot

An Ansible role that installs, upgrades and configures the RCBot2 plugin for Day of Defeat: Source.

For more information please check this project's official web page: <http://rcbot.bots-united.com>

## Requirements

An ansible role dedicated to the installation of SteamCMD such as [ansible-steamcmd](https://github.com/tleguern/ansible-steamcmd).

An ansible role dedicated to the Installation of Metamod:Source such as [ansible-role-metamod-source](https://github.com/tleguern/ansible-role-metamod-source).

An ansible role dedicated to the installation of Day of Defeat: Source such as [ansible-role-dod-source](https://github.com/tleguern/ansible-role-dod-source).

## Role Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `steamcmd_user` | User name for steamcmd | `steam` |
| `rcbot2_url` | Download mirror | `https://github.com/APGRoboCop/rcbot2/releases/download/` |
| `rcbot2_version` | RCBot2 version, consider this option to be read only | `1.4` |
| `rcbot2_target` | Archive name | `rcbot2_linux.tar.gz` |
| `rcbot2_install_path` | Installation directory | `/home/{{ steamcmd_user }}/.steam/steamapps/common/Day of Defeat Source Dedicated Server/dod` |
| `rcbot2_config` | Main configuration file content | `""` |
| `rcbot2_waypoints_directory` | Local directory containing waypoints for the bots | `""` |

### `rcbot2_config`

This variable holds the content of the main configuration file.

Example:

```yaml
rcbot2_config: |
  rcbot_supermode 1
  rcbot_ffa 1
  ...
```

Default values are available [here](https://github.com/APGRoboCop/rcbot2/blob/master/package/config/config.ini).

## Dependencies

None.

## Example Playbook

```yaml
- hosts: game
  vars:
    rcbot2_waypoints_directory: files/dod-source/waypoints
  pre_tasks:
    - package:
        name: acl
        state: present
  roles:
    - role: tleguern.steamcmd
    - role: tleguern.dod-source
    - role: tleguern.metamod-source
    - role: tleguern.dod-source-rcbot2
```

## License

ISC

## Contributing

Either send [send GitHub pull requests](https://github.com/tleguern/ansible-role-dod-source-rcbot2) or [send patches on SourceHut](https://lists.sr.ht/~tleguern/misc).

## Author Information

Tristan Le Guern <tleguern@bouledef.eu>
