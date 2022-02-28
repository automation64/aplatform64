---
title: "Ansible Role: serdigital64.system.sys_dconf"
description: "Manage provisioning of the DConf service"
authors:
  - SerDigital64
tags:
  - ansible
  - system
  - linux
  - automation
---

# Ansible Role: serdigital64.system.sys_dconf

## Purpose

Manage provisioning of the DConf service.

Supported features in the current version:

- Prepare environment for application deployment.
- Deploy application. Packages are defined in the variable `sys_dconf_profiles`.
- Configure application:
  - Create user profile definition
- Provision default local DBs for the user profile

The **sys_dconf** Ansible-Role is part of the [A:Platform64](https://github.com/serdigital64/aplatform64) project and is available in the [system](../collections/system.md) Ansible-Collection.

## Usage

The following example is an **Ansible Playbook** that includes all the supported features:

[use this link if viewing the doc on github](../../collections/serdigital64/system/playbooks/sys_dconf.yml)

```yaml
{% include "../../collections/serdigital64/system/playbooks/sys_dconf.yml" %}
```

The playbook can be run by executing:

```shell
# Set ANSIBLE_COLLECTIONS_PATHS to the default location. Change as needed.
ANSIBLE_COLLECTIONS_PATHS="${HOME}/.ansible/collections"
ansible-playbook "${ANSIBLE_COLLECTIONS_PATHS}/ansible_collections/serdigital64/system/playbooks/sys_dconf.yml"
```

## Role Parameters

### Actions

- Use **action-parameters** to control what tasks are enabled for the role to execute.
- Parameters should be declared as task level vars as they are intented to be dynamic.

```yaml
sys_dconf:
  resolve_prereq:
  prepare:
  deploy:
  setup:
  provision:
sys_dconf_db_local:
  - source:
    name:
```

| Parameter                   | Required?      | Type    | Default | Purpose / Value                               |
| --------------------------- | -------------- | ------- | ------- | --------------------------------------------- |
| sys_dconf.resolve_prereq    | no             | boolean | `false` | Enable automatic resolution of prequisites    |
| sys_dconf.prepare           | no             | boolean | `false` | Enable environment preparation                |
| sys_dconf.deploy            | no             | boolean | `false` | Enable installation of application packages   |
| sys_dconf.setup             | no             | boolean | `false` | Enable application configuration              |
| sys_dconf.provision         | no             | boolean | `false` | Enable provisioning of application components |
| sys_dconf_db_local          | yes(provision) | list    |         | List of local dbs                             |
| sys_dconf_db_local.0.source | yes            | string  |         | Full path to the source db                    |
| sys_dconf_db_local.0.name   | yes            | string  |         | DB name                                       |

### End State

- Use **end-state** parameters to define the target state after role execution.
- Parameters should be declared in **host_vars** or **group_vars** as they are intended to be permanent.

```yaml

```

| Parameter | Required? | Type | Default | Purpose / Value |
| --------- | --------- | ---- | ------- | --------------- |

## Deployment

### OS Compatibility

- CentOS8
- OracleLinux8
- Ubuntu20
- Ubuntu21
- Fedora33
- Fedora35
- Debian10
- Debian11

### Dependencies

- Ansible Collections:
  - serdigital64.backup
    - bkp_archive
  - serdigital64.system
    - sys_package
    - sys_repository

### Prerequisites

The Ansible engine must be already installed and configured for privileged access and remote execution.

In addition the following prerequisites can be automatically solved when running the playbook by setting the role action: `resolve_prereq: true`

- Package manager for the target application is installed and enabled.

### Installation Procedure

Manually install Ansible Collections from the Ansible Galaxy repository:

```shell
ansible-galaxy collection install serdigital64.system
```

Automatic installation is also available by deploying [A:Platform64](https://aplatform64.readthedocs.io/en/latest/#deployment)

## Contributing

Help on implementing new features and maintaining the code base is welcomed.

Please see the [guidelines](../contributing/guidelines.md) for further details.

## Author

- [SerDigital64](https://serdigital64.github.io/)

## License

[GPL-3.0-or-later](https://www.gnu.org/licenses/gpl-3.0.txt)