# yauh.base
Ansible role for basic configuration settings

## Requirements
SSH access to the remote machine

## Role Variables
`deployment_user` is the name of the user that will be used for all ansible-activioty on the remote machine. In order to set their password use use mkpasswd --method=SHA-512`to create passwords. The default password is`password`. The`deployment_user`is also able to execute`sudo`. By default the current user's public key will also be added to the remote server for the`deployment_user`.

`base_install_packages` contains a list of packages that are part of the base installation of the server.

`timezone` is the timezone used for the server's internal time and date.

```
deployment_user: ansible # user on remote system used for deployments
deployment_user_password: $1$d7dSH$lyCQtZG3NoWhJyVNCWxpO1 # password
root_user_password: $1$d7dSH$lyCQtZG3NoWhJyVNCWxpO1 # password

authorized_keys:
  - public_key: "{{ lookup('file', '~/.ssh/id_rsa.pub') }}"

base_install_packages:
  - sudo
  - openssh-server
  - ntp
  - ssh
  - vim
  - locate
  - debian-keyring
  - debian-archive-keyring
  - ca-certificates
  - language-pack-en
timezone: Europe/Berlin
```

## Dependencies
None

## Example Playbook
Usage in a playbook via roles:

```
- hosts: all
  roles:
     - { role: yauh.base }
```

## License
BSD

## Author Information
Stephan Hochhaus stephan@yauh.de

[https://github.com/yauh](https://github.com/yauh)
