<!-- BEGIN_ANSIBLE_DOCS -->
# Ansible Role: calopsys.observability.alloy
Version: 1.0.0

This role installs, manages and configures a alloy instance on Debian systems.


## Requirements

| Platform | Versions |
| -------- | -------- |
| Debian | all |

## Role Arguments


### Entrypoint: main

Install and configure a alloy instance on Debian systems.

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| calopsys_alloy_user | The unix user to run alloy as. | str | no | alloy |
| calopsys_alloy_group | The primary group of the alloy user. | str | no | {{ calopsys_alloy_user }} |
| calopsys_alloy_config_template | Local path to the alloy configuration template. | str | no | minimal.j2 |
| calopsys_alloy_config_dir | Absolute path to the alloy configurations directory. | str | no | /etc/alloy |
| calopsys_alloy_env_template | Local path to the alloy environment config file. | str | no | default_env.j2 |
| calopsys_alloy_env_dir | Absolute path to the environment configurations directory. | str | no | /etc/default |
| calopsys_alloy_prometheus_endpoint_url | Required when using config templates provided by the role, url of the prometheus endpoint to remote_write to. | str | no |  |
| calopsys_alloy_loki_endpoint_url | Required when using config templates provided by the role, url of the loki endpoint to send logs to. | str | no |  |



## Dependencies
None.

## Example Playbook

```
- hosts: all
  tasks:
    - name: Importing role: calopsys.observability.alloy
      ansible.builtin.import_role:
        name: calopsys.observability.alloy
      vars:
```

## License

MIT

## Author and Project Information
Calopsys @ Calopsys

Issues: [tracker](https://github.com/calopsys/ansible-collection-observability/issues)
<!-- END_ANSIBLE_DOCS -->
