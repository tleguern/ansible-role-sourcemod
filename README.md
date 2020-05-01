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
| `sourcemod_admins_simple` | SourceMod admin declaration via the flat file format | See bellow |
| `sourcemod_plugins` | List of plugins to enable or disable | See bellow |

### `sourcemod_admins_simple`

A list of hashes containing the identity and flags of any server administrator.
Optionnaly immunity levels and password can be suplied.

| Key | Description |
|-----|-------------|
| `identity` | A SteamID3 formatted SteamID, a bang-prefixed IP address or a simple name |
| `flags` | Letter encoded permission levels |
| `immunity` | Immunity level |
| `password` | Password, only for somple name `identity` |

More information [here](https://wiki.alliedmods.net/Adding_Admins_(SourceMod)).

Example:

```
sourcemod_admins_simple:
  - identity: STEAM_0:1:16
    flags: bce
  - identity: "!127.0.0.1"
    immunity: "99"
    flags: z
  - identity: BAILOPAN
    flags: abc
    password: Gab3n
```

## `sourcemod_plugins`

Allows to enable or disable any installed plugins.

| Key | Description |
|-----|-------------|
| `name` | The plugin's name without file suffix |
| `state` | Only `disabled` or `enabled` |

Example:

```
sourcemod_plugins:
  - name: mapchooser
    state: enabled
  - name: disable
    state: enabled
  - name: funcommands
    state: disable
```

# Dependencies

None

# Example Playbook

```yaml
- hosts: game
  vars:
   sourcemod_admins_simple:
     - identity: STEAM_0:1:16
       flags: z
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
