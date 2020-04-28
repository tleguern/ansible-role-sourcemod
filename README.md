# Ansible Role: sourcemod

An Ansible role that installs and configures [SourceMod](https://www.sourcemod.net/), a [Metamod:Source](http://www.metamodsource.net/) plugin.

## Requirements

An ansible role dedicated to the installation of SteamCMD such as [ansible-steamcmd](https://github.com/Aversiste/ansible-steamcmd) or any role providing the `{{ steamcmd_user }}` variable.

An ansible role dedicated to the installation of a Source mod such as [ansible-role-cstrike-source](https://github.com/Aversiste/ansible-role-cstrike-source) or any role providing the `Restart {{ metamod_source_game }}` handler.

An ansible role dedicated to the Installation of Metamod:Source such as [ansible-role-metamod-source](https://github.com/Aversiste/ansible-role-metamod-source), or any role providing the `{{ metamod_source_install_path }}`,

## Role Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `steamcmd_user` | User name for steamcmd | `steam` |
| `sourcemod_url` | URL pointing to sourcemod releases | `https://sm.alliedmods.net/smdrop` |
| `sourcemod_branch` | Release branch (should generally be the same as `{{ metamod_source_branch }}` | `1.10` |
| `metamod_source_install_path` | Installation directory | mandatory |

# Dependencies

None

# Example Playbook

```yaml
- hosts: game
  roles:
    - role: ansible-steamcmd
    - role: ansible-role-cstrike-source
    - role: ansible-role-metamod-source
    - role: ansible-role-sourcemod
```

# License

```
Copyright (c) 2020 Tristan Le Guern <tleguern@bouledef.eu>

Permission to use, copy, modify, and distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```

# Author Information

Tristan Le Guern <tleguern@bouledef.eu>
