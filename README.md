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

## Usage

### Linux

```
ansible-playbook playbook.yml
```

### Non-linux
You will need Vagrant alongside Virtualbox.

```
vagrant up
```

```
ansible-playbook playbook.yml
```

## Acknowledgments
* https://www.willhaley.com/blog/custom-debian-live-environment/
* https://github.com/dinooz/denos