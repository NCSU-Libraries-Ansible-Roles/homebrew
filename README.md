# Homebrew

Installs Homebrew (Linuxbrew) and dependencies.


## Variables

* `homebrew_user` - The user that will own Homebrew (default: `deploy`)
* `homebrew_group` - The group that will own Homebrew (default: `deploy`)

Any package installed via Homebrew will be owned by `homebrew_user`:`homebrew_group`. This means:

1. Neither of these should be `root` (Homebrew install will fail if run as root).

2. Any process that needs to use a Homebrew-managed package needs to be run by `homebrew_user` or a user in `homebrew_group`

If Homebrew-managed packages will be called by a Rails app owned by `deploy:deploy`, the defaults will be OK.

For Vagrant, include the role like this to make `vagrant:vagrant` the owner:

```
- role: homebrew
  homebrew_user: 'vagrant'
  homebrew_group: 'vagrant'
```

Replace `homebrew_user` and `homebrew_group` values as needed for other situtions.


## After Homebrew is installed

After this role has executed in an Ansible playbook, the following Ansible modules can be used:

* [homebrew](https://docs.ansible.com/ansible/latest/modules/homebrew_module.html)
* [homebrew_cask](https://docs.ansible.com/ansible/latest/modules/homebrew_cask_module.html)
* [homebrew_tap](https://docs.ansible.com/ansible/latest/modules/homebrew_tap_module.html)
