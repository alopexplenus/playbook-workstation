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

The inventory is checked in and targets only `localhost` in the `[desktop]`
group; `ansible.cfg` picks it up automatically.

## Tailscale access

The playbook installs and starts Tailscale. Enroll the host manually into the
tailnet:

```bash
sudo tailscale up
```
