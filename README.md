Ansible Role: Filesystem
======================================

[![Build Status](https://travis-ci.org/entercloudsuite/ansible-filesystem.svg?branch=master)](https://travis-ci.org/entercloudsuite/ansible-filesystem)
[![Galaxy](https://img.shields.io/badge/galaxy-lorenzocomotti.ansible_filesystem-blue.svg?style=flat-square)](https://galaxy.ansible.com/lorenzocomotti/ansible_filesystem)

Creating partition, filesystem and mounting it

## Requirements

This role requires Ansible 2.2 or higher.

## Role Variables

Refer to https://github.com/AerisCloud/ansible-disk

## Filesystem Playbook

Run with default vars:

```
- hosts: all
  roles:
    - role: entercloudsuite.filesystem
      disk_additional_disks:
        - disk: /dev/vdb
          fstype: xfs
          mount_options: defaults
          mount: /example
          disable_periodic_fsck: false
```

## Testing

Tests are performed using [Molecule](http://molecule.readthedocs.org/en/latest/).

1. Run `molecule create` to start the target Docker container on your local engine.  
2. Use `molecule login` to log in to the running container.  
3. Edit the role files.  
4. Add other required roles (external) in the molecule/default/requirements.yml file.  
5. Edit the molecule/default/playbook.yml.  
6. Define infra tests under the molecule/default/tests folder using the goos verifier.  
7. When ready, use `molecule converge` to run the Ansible Playbook and `molecule verify` to execute the test suite.  
Note that the converge process starts performing a syntax check of the role.  
Destroy the Docker container with the command `molecule destroy`.   

To run all the steps with just one command, run `molecule test`.  

## License

MIT
