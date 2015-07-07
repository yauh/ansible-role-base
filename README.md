# yauh.base
Ansible role for fundamental server configuration and set up

## Requirements
SSH access to the remote machine

## Role Variables
`ssh_users` is an array of users with a `name` and `key` attribute. `name` is the name of the local user on the server, `key` contains a reference to a public ssh key. All users from this array will be able to perform the `sudo` command.

`timezone` is the timezone used for the server's internal time and date.

```
ssh_users:
  - name: ansible
    key: "{{ lookup('file', '~/.ssh/id_rsa.pub') }}"
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
