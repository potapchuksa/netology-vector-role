Role Name
=========

Ansible role for installing and configuring [Vector](https://vector.dev/) log aggregator.

Requirements
------------

- Ansible >= 2.9
- Target OS: Linux with systemd
- Python >= 3.6 on target hosts

Role Variables
--------------

| Variable | Default | Description |
|----------|---------|-------------|
| `vector_version` | `"0.40.0"` | Version of Vector to install |
| `vector_arch` | `"x86_64-unknown-linux-musl"` | Target architecture for download |
| `vector_install_dir` | `"/usr/local/bin"` | Directory for Vector binary |
| `vector_config_dir` | `"/etc/vector"` | Directory for configuration files |
| `vector_data_dir` | `"/var/lib/vector"` | Directory for Vector data/storage |
| `vector_config_file` | `"{{ vector_config_dir }}/vector.yml"` | Path to main config file |
| `vector_download_url` | `"https://github.com/vectordotdev/vector/releases/download/v{{ vector_version }}/vector-{{ vector_version }}-{{ vector_arch }}.tar.gz"` | Full URL for downloading Vector archive |
| `clickhouse_host` | `"{{ hostvars['clickhouse-01']['ansible_host'] \| default('localhost') }}"` | ClickHouse server hostname/IP |
| `clickhouse_port` | `8123` | ClickHouse HTTP port |
| `clickhouse_database` | `"logs"` | Target database name |
| `clickhouse_table` | `"vector_logs"` | Target table name |

Dependencies
------------

None.

Example Playbook
----------------

```yaml
- hosts: servers
  become: true
  roles:
    - vector-role
```

License
-------

MIT

Author Information
------------------

Sergey Potapchuk
