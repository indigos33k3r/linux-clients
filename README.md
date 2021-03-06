# Linux Clients

This repo contains the ansible configuration to deploy a linux client.

## Usage

Tasks that have to be done before ansible can manage the workstation:

- Install the system using Fedora, Debian or Ubuntu
  - Use german keyboard layout and language
  - Create a user `sysadmin` and make him an admin (Fedora: member of `wheel` / Debian: `sudo` group) (Password should be well known to admins)
- (Install and) start the ssh deamon
- Edit `/etc/sudoers` and allow members of group `wheel` to gain root without password: `sudo visudo`
- Fedora: You have to do an `dnf upgrade` and accept the PGP keys before the playbook is working completely

### Deploy ansible playbook

- `ansible-playbook <group file>.yml [--diff]`
Test and simulate playbook with `--check`
Get debug output with `-vvv`

#### for workstations

- Set the hostname to `fablab-ws%d%d.lab.fablab.uni-erlangen.de`
- Make sure this hostname is correctly configured on the DHCP server (TODO provision dhcp server, too and automate this step)
- deploy with `ansible-playbook workstations.yml [--diff]`

#### for messe notebook

- instead, deploy with `ansible-playbook messenotebook.yml [--diff]`

## After provisioning

- reboot
- start VisiCut and download the settings
- messe notebook: change VisiCut camera setting to http://localhost:9999/image
- set KDE desktop to "folder view" so that desktop icons are shown
- setup Inkscape shortcut Alt-L for "Open in VisiCut"

## TODO:

- configure printers

## License

[GPLv3](https://www.gnu.org/licenses/gpl.html)
