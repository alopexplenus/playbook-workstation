Ansible playbook that sets up my desktop workstation. It:

* installs my current set of tools
* installs the dotfiles manager [yadm](https://github.com/TheLocehiliosan/yadm)
* clones a dotfiles repo
* installs and starts Tailscale

## Requirements

* Ansible, which can be installed in a few ways, such as:
  * ```apt install ansible```
  * ```dnf install ansible```
  * ```python -m pip install ansible```

### Run

From the playbook directory:

```
ansible-playbook workstation.yaml --ask-become-pass
```

Copy `inventory.ini.example` to `inventory.ini` (the only group is
`[desktop]`, aimed at localhost). The local inventory is ignored by Git.

## Tailscale access

The playbook installs and starts Tailscale. Enroll the host manually into the
tailnet:

```bash
sudo tailscale up
```

## OpenCode clients on the trusted LAN

When consuming an OpenCode server provisioned by the separate infra repo, set
the workstation overrides used by the `wk` helper:

```bash
export WK_OPENCODE_LAN_URL=http://LAN_HOST:4096
export WK_OPENCODE_TAILSCALE_URL=http://TAILSCALE_HOST:4096
```

`WK_OPENCODE_LAN_URL` is checked first and `WK_OPENCODE_TAILSCALE_URL` is the
fallback. These settings contain endpoints only; the server password is
configured on the server side and is entered interactively by
`wk --remote PROJECT`.
