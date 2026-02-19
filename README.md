# Calopsys Ansible Collection - Observability

An Ansible collection for deploying and managing the Grafana LGTM observability stack (Loki, Grafana, Mimir) and Alloy collector on Debian systems.

## Roles

| Role | Description |
|------|-------------|
| `calopsys.observability.alloy` | Grafana Alloy - unified telemetry collector for metrics, logs, and traces |
| `calopsys.observability.grafana` | Grafana - visualization and analytics platform |
| `calopsys.observability.loki` | Grafana Loki - log aggregation system |
| `calopsys.observability.mimir` | Grafana Mimir - Prometheus-compatible metrics backend |

## Requirements

- Ansible Core >= 2.18.0
- Target: Debian-based systems

## Installation

Create a `galaxy_requirements.yml` file:

```yaml
collections:
  - name: git@github.com:calopsys/ansible-collection-observability.git
    type: git
    version: "1.0.0"
```

Then run:
```bash
ansible-galaxy install -r galaxy_requirements.yml
```

## Usage

### Grafana Alloy

Deploy the Alloy collector to ship metrics and logs to your backends:

```yaml
- name: "Deploy Grafana Alloy."
  hosts: all
  roles:
    - role: calopsys.observability.alloy
      vars:
        calopsys_alloy_config_template: minimal.j2
        calopsys_alloy_prometheus_endpoint_url: "http://mimir:9009/api/v1/push"
        calopsys_alloy_loki_endpoint_url: "http://loki:3100/loki/api/v1/push"
```

### Grafana Loki

Deploy Loki for log aggregation:

```yaml
- name: "Deploy Grafana Loki."
  hosts: all
  roles:
    - role: calopsys.observability.loki
      vars:
        calopsys_loki_config_template: standalone_s3.yml.j2
        calopsys_loki_standalone_s3_endpoint: "https://s3.example.com"
        calopsys_loki_standalone_s3_bucket: "loki-data"
        calopsys_loki_standalone_s3_accesskey: "{{ s3_access_key }}"
        calopsys_loki_standalone_s3_secretkey: "{{ s3_secret_key }}"
        calopsys_loki_standalone_retention_period: "365d"
```

### Grafana Mimir

Deploy Mimir for metrics storage:

```yaml
- name: "Deploy Grafana Mimir."
  hosts: all
  roles:
    - role: calopsys.observability.mimir
      vars:
        calopsys_mimir_config_template: standalone_s3.yml.j2
        calopsys_mimir_standalone_s3_endpoint: "https://s3.example.com"
        calopsys_mimir_standalone_s3_bucket: "mimir-data"
        calopsys_mimir_standalone_s3_accesskey: "{{ s3_access_key }}"
        calopsys_mimir_standalone_s3_secretkey: "{{ s3_secret_key }}"
```

### Grafana

Deploy Grafana for visualization. You must provide your own configuration templates:

```yaml
- name: "Deploy Grafana."
  hosts: all
  roles:
    - role: calopsys.observability.grafana
      vars:
        calopsys_grafana_config_template: path/to/grafana.ini.j2
```

## Role Variables

Each role has its own set of variables documented in the respective `REFERENCE.md` files:

- [Alloy](roles/alloy/REFERENCE.md)
- [Grafana](roles/grafana/REFERENCE.md)
- [Loki](roles/loki/REFERENCE.md)
- [Mimir](roles/mimir/REFERENCE.md)

## Development

### Testing
```bash
make test.sanity              # Run ansible-test sanity
make molecule                 # Run molecule tests for all roles
make molecule role=grafana    # Run molecule tests for a specific role
make test                     # Run lint, sanity, and molecule tests
```

Molecule tests use podman and include idempotency verification (runs the role twice to ensure no changes on second run).

### Building
```bash
make build
```

### Documentation
```bash
make docs
make docs role=alloy
```

## License

MIT License - see [LICENSE](LICENSE) for details.
