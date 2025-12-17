Ansible playbook that:

* installs my current set of tools
* installs the dotfiles manager [yadm](https://github.com/TheLocehiliosan/yadm)
* clone a dotfiles repo

## Requirements

* Ansible, which can be installed in a few ways, such as:
  * ```apt install ansible```
  * ```dnf install ansible```
  * ```python -m pip install ansible```
    
### Run

From the playbook directory:

```
# install and clone on local system
ansible-playbook main.yaml --connection=local --ask-become-pass

# on remote systems (make sure to update the inventory)
ansible-playbook main.yaml
```
