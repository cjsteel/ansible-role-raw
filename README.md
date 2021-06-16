[raw](#raw)
=========

<img src="https://docs.ansible.com/ansible-tower/3.2.4/html_ja/installandreference/_static/images/logo_invert.png" width="10%" height="10%" alt="Ansible logo" align="right"/>
<a href="https://travis-ci.org/cjsteel/ansible-role-raw"> <img src="https://travis-ci.org/cjsteel/ansible-role-raw.svg?branch=master" alt="Build status"/></a> <img src="https://img.shields.io/ansible/role/d/"/> <img src="https://img.shields.io/ansible/quality/"/>

<a href="https://github.com/cjsteel/ansible-role-raw/actions"><img src="https://github.com/cjsteel/ansible-role-raw/workflows/GitHub%20Action/badge.svg"/></a>

An Ansible role for running raw commands on one or more remote systems. Originally created to "Faire table rase" on the default firewalld configuration for Fedora 34 but should be usable anytime you need to run a series of adhoc commands on one or more Ansible targets using the Ansible shell module.

Example Playbook
----------------

This example is taken from `molecule/resources/playbook.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    # requirements
    # - role: roberdebock.bootstrap
    # raw
    - role: cjsteel.raw
    #  vars:
    #    - raw_
        
```

The machine you are running this on, may need to be prepared, I use this playbook to ensure everything is in place to let the role work.

```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: roberdebock.bootstrap
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use roles based on Robert de Bocks beautiful role patterns.

Role Variables
--------------
* [./defaults/main.yml](./defaults/main.yml)

`defaults/main.yml` 
```yaml
---
# defaults file for raw
```

Requirements
------------

- Access to a repository containing any required packages.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

Requirements (other galaxy roles) can be installed by running the following from the projects ansible directory:

```shell
ansible-galaxy install -r requirements.yml
```

Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/raw.png "Dependency")


Compatibility
-------------

This role has been tested on these [container images](https://hub.docker.com/):

|container|tags|
|---------|----|
|alpine|all|
|debian|all|
|el|7, 8|
|fedora|all|
|opensuse|all|
|ubuntu|bionic|

The minimum version of Ansible required is 2.7 but tests have been done to:

- The previous version, on version lower.
- The current version.
- The development version.

Testing (not implemented at this time)
-------

[Unit tests](https://travis-ci.org/cjsteel/ansible-role-raw) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/cjsteel/ansible-role-raw/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```shell
molecule test
```

Alternatives:

```shell
# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```



Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `cjsteel`, image: `fedora`, tag: `latest`) tests:

```shell
tox
```

Alternatives

```shell
# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

License
-------

Apache-2.0


Author Information
------------------

[Robert de Bock](https://robertdebock.nl)

## Customizations

[Christopher Steel](https://cjsteel.github.io)
