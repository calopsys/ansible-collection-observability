<!-- BEGIN_ANSIBLE_DOCS -->
# Ansible Role: calopsys.observability.grafana
Version: 1.0.0

This role installs, manages and configures a grafana instance on Debian systems.


## Requirements

| Platform | Versions |
| -------- | -------- |
| Debian | all |

## Role Arguments


### Entrypoint: main

Install and configure a grafana instance on Debian systems.

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| calopsys_grafana_config_dir | Absolute path to the grafana configuration directory. | str | no | /etc/grafana |
| calopsys_grafana_config_template | Local path to the grafana.ini configuration template. | str | no |  |
| calopsys_grafana_provisioning | List of provisioning resources to deploy. | list of 'dict' | no | [] |



## Dependencies
None.

## Example Playbook

```
- hosts: all
  tasks:
    - name: Importing role: calopsys.observability.grafana
      ansible.builtin.import_role:
        name: calopsys.observability.grafana
      vars:
```

## License

MIT

## Author and Project Information
Calopsys @ Calopsys

Issues: [tracker](https://github.com/calopsys/ansible-collection-observability/issues)
<!-- END_ANSIBLE_DOCS -->
