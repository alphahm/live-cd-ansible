# Live CD Ansible

This project is inspired by a couple of helpful guides, cited below in Acknowledgments, showing
how to build your own Live CD.
Those guides are great, this project is just a more automated way to achieve the same. It uses
Ansible and optionally Vagrant when not using a Linux machine.

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

Add needed information depending on your envrinoment setup.

Example:

```yaml
---
hosts: localhost
working_folder: /home/<your username>/live_cd
user: <your username>
group: <your group>
```

* Run playbook

```
ansible-playbook playbook.yml
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
working_folder: /home/vagrant/live_cd
user: vagrant
group: vagrant
```

* Run playbook.

```
ansible-playbook playbook.yml
```

## Acknowledgments
* https://www.willhaley.com/blog/custom-debian-live-environment/
* https://github.com/dinooz/denos