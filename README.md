# ansible-dotfiles

See [ARCH.md](ARCH.md) for the barebones system installation

On a clean arch installation, as root (or with sudo) run the following (the playbook
will prompt for the user password)

```bash
pacman -Syu ansible git
git clone https://github.com/nayaverdier/ansible-dotfiles.git
ansible-playbook ansible-dotfiles/setup.yml --extra-vars "install_model=dell-xps-7590"
```

The `install_model` variable defaults to `virtualbox`

After the ansible playbook is run for the first time, it creates a
`setup-dell-xps-7590` (or similar) script within `/usr/local/bin` that can be
invoked directly (with sudo) rather than calling ansible.

For example:

```bash
sudo setup-dell-xps-7590

sudo setup-dell-xps-7590 --diff # to show the changes being made
sudo setup-dell-xps-7590 --check --diff # dry run and show the expected changes
sudo setup-dell-xps-7590 --tags zsh # only run tasks with a particular tag
```

## Credits

- [`library/aur`](https://github.com/kewlfft/ansible-aur)
