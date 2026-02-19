<!-- BEGIN_ANSIBLE_DOCS -->
# Ansible Role: calopsys.observability.loki
Version: 1.0.0

This role installs, manages and configures a loki instance on Debian systems.


## Requirements

| Platform | Versions |
| -------- | -------- |
| Debian | all |

## Role Arguments


### Entrypoint: main

Install and configure a loki instance on Debian systems.

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| calopsys_loki_env_dir | Remote path to the directory containing environment configs. | str | no | /etc/default |
| calopsys_loki_config_dir | Remote path to the loki configurations directory. | str | no | /etc/loki |
| calopsys_loki_config_template | Local path to the loki configuration template. | str | no |  |
| calopsys_loki_env_template | Local path to the loki environment config template. | str | no |  |
| calopsys_loki_standalone_retention_period | When using the standalone template, configure the log retention period. Defaults to 1 month. | str | no | 365d |
| calopsys_loki_standalone_s3_endpoint | When using the standalone template, the S3 endpoint. | str | no |  |
| calopsys_loki_standalone_s3_accesskey | When using the standalone template, the S3 accesskey. | str | no |  |
| calopsys_loki_standalone_s3_secretkey | When using the standalone template, the S3 secretkey. | str | no |  |
| calopsys_loki_standalone_s3_bucket | When using the standalone template, the S3 bucket. | str | no |  |
| calopsys_loki_standalone_log_level | Required when using the 'standalone_s3' template, specifies the log level for the loki daemon. | str | no | warn |



## Dependencies
None.

## Example Playbook

```
- hosts: all
  tasks:
    - name: Importing role: calopsys.observability.loki
      ansible.builtin.import_role:
        name: calopsys.observability.loki
      vars:
```

## License

MIT

## Author and Project Information
Calopsys @ Calopsys

Issues: [tracker](https://github.com/calopsys/ansible-collection-observability/issues)
<!-- END_ANSIBLE_DOCS -->
