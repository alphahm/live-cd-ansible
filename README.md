# Live CD Ansible

This project is inspired by a couple of helpful guides, cited below in Acknowledgments, showing
how to build your own Live CD.
Those guides are great, this project is just a more automated way to achieve the same. It uses
Ansible and optionally Vagrant when not running on a Linux machine.

This playbook will install Debian Bookworm (12) with Gnome Desktop Manager but this can be
customised to install another distribution and/or desktop manager.

## Installation

```
python3 -m virtualenv venv
source venv/bin/activate
pip install -r requirements.txt
```

Install Vagrant and VirtualBox if running on a non-Linux OS.

## Usage

### Linux

* Copy `vars.yml.dist` to `vars.yml`.

```
cp vars.yml.dist vars.yml
```

Add needed information depending on your environment setup.

Example:

```yaml
---
hosts: localhost
working_folder: /home/<your username>/live_cd
destination_folder: /home/<your username>/live_cd_iso
user: <your username>
group: <your group>
user_password: <live cd user password>
root_password: <live cd root password>
debian_mirror: <closest mirror link, pick one form https://www.debian.org/mirror/list>
```

* Run playbook

```
source venv/bin/activate
ansible-playbook playbook.yml --ask-become-pass
```

### Non-linux
* You will need Vagrant alongside Virtualbox.

```
vagrant up
```

* Copy `vars.yml.dist` to `vars.yml` and add needed information.

```yaml
---
hosts: vagrant
working_folder: /home/vagrant/live_cd_install
destination_folder: /home/vagrant/live_cd
user: vagrant
group: vagrant
user_password: <live cd user password>
root_password: <live cd root password>
debian_mirror: <closest mirror link, pick one form https://www.debian.org/mirror/list>
```

* Run playbook.

```
source venv/bin/activate
ansible-playbook playbook.yml
```

When done, to shutdown Vagrant machine, run:

```
vagrant halt
```

## Acknowledgments
* https://www.willhaley.com/blog/custom-debian-live-environment/
* https://github.com/dinooz/denos