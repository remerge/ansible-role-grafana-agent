# Ansible Role for Grafana Agent

Install and Configure [Grafana Agent](https://github.com/grafana/agent) with
Ansible.

The [Contributing Guide](CONTRIBUTING.md) explains how to work with and
contribute to this repository.

## Example Playbook

```yaml
---
- name: converge
  hosts: all
  become: yes
  gather_facts: yes
  roles:
    - role: remerge.grafana_agent
```

## Role Variables

These variables are set in `defaults/main.yml`:

```yaml
---
grafana_agent_wal_directory: /var/lib/grafana-agent
grafana_agent_positions_directory: /var/lib/promtail

grafana_agent_server_http_address: "127.0.0.1:9090"
grafana_agent_server_grpc_address: "127.0.0.1:9091"

grafana_agent_config:
  metrics:
    global:
      scrape_interval: 1m
    wal_directory: "{{ grafana_agent_wal_directory }}"
    configs: []
  integrations:
    agent:
      enabled: true
      instance: "{{ inventory_hostname }}"
    node_exporter:
      enabled: true
      instance: "{{ inventory_hostname }}"
      include_exporter_metrics: true
      disable_collectors:
        - mdadm
```
