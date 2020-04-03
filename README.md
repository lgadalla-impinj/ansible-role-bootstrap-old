# bootstrap

Prepare your system to be managed by Ansible.


[![github](https://github.com/lgadalla-impinj/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/lgadalla-impinj/ansible-role-bootstrap/actions)

## Example Playbook

This example is taken from `molecule/resources/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - impinj.bootstrap
```

The machine may need to be prepared using `molecule/resources/prepare.yml`:
```yaml
No preparation required.
```

For verification `molecule/resources/verify.yml` run after the role has been applied.
```yaml
---
- name: Verify
  hosts: all
  become: no
  gather_facts: yes

  tasks:
    - name: test connection
      ping:
```

## Role Variables

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for bootstrap

# The user to use to connect to machines.
bootstrap_user: root

# Do you want to wait for the host to be available?
bootstrap_wait_for_host: no

# The number of seconds you want to wait during connection test before failing.
bootstrap_timeout: 3

# The number of retries during installation
bootstrap_retries: 3
```

## Requirements

- Access to a repository containing packages, likely on the Internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
- none
```

## Context

This role is a part of many compatible roles.

## Compatibility

This role has been tested on these [container images](https://hub.docker.com/):

|container|tags|
|---------|----|
|amazon|all|
|alpine|all|
|debian|all|
|el|7, 8|
|fedora|all|
|opensuse|all|
|ubuntu|bionic|

The minimum version of Ansible required is 2.8 but tests have been done to:

- The previous version, on version lower.
- The current version.
- The development version.



## Testing

[Unit tests](https://travis-ci.com/lgadalla-impinj/ansible-role-bootstrap) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/lgadalla-impinj/ansible-role-bootstrap/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```
molecule test

# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```

Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `robertdebock`, image: `fedora`, tag: `latest`) tests:

```
tox

# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

## License

Apache-2.0


## Author Information

Author: Impinj DevOps (it_devops_team@impinj.com)
