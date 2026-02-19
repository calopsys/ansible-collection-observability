<!-- BEGIN_ANSIBLE_DOCS -->
# Ansible Role: calopsys.observability.mimir
Version: 1.0.0

This role installs, manages and configures a mimir instance on Debian systems.


## Requirements

| Platform | Versions |
| -------- | -------- |
| Debian | all |

## Role Arguments


### Entrypoint: main

Install and configure a mimir instance on Debian systems.

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| calopsys_mimir_config_dir | Absolute path to the mimir configuration directory. | str | no | /etc/mimir |
| calopsys_mimir_config_template | Local path to the configuration template. | str | no |  |
| calopsys_mimir_env_dir | Absolute path to the directory containing environment configurations. | str | no | /etc/default |
| calopsys_mimir_env_template | Local path to the env file template. | str | no |  |
| calopsys_mimir_standalone_tenant_name | Required when using the 'standalone_s3' template, specifies the tenant name. | str | no | anonymous |
| calopsys_mimir_standalone_s3_endpoint | Required when using the 'standalone_s3' template, specifies the s3 endpoint. | str | no |  |
| calopsys_mimir_standalone_s3_accesskey | Required when using the 'standalone_s3' template, specifies the s3 access key. | str | no |  |
| calopsys_mimir_standalone_s3_secretkey | Required when using the 'standalone_s3' template, specifies the s3 secret key. | str | no |  |
| calopsys_mimir_standalone_s3_bucket | Required when using the 'standalone_s3' template, specifies the s3 bucket. | str | no |  |
| calopsys_mimir_standalone_log_level | Required when using the 'standalone_s3' template, specifies the log level for the mimir daemon. | str | no | warn |



## Dependencies
None.

## Example Playbook

```
- hosts: all
  tasks:
    - name: Importing role: calopsys.observability.mimir
      ansible.builtin.import_role:
        name: calopsys.observability.mimir
      vars:
```

## License

MIT

## Author and Project Information
Calopsys @ Calopsys

Issues: [tracker](https://github.com/calopsys/ansible-collection-observability/issues)
<!-- END_ANSIBLE_DOCS -->
