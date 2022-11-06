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
grafana_agent_server_http_address: "127.0.0.1:9090"
grafana_agent_server_grpc_address: "127.0.0.1:9091"
grafana_agent_config: {}
```

This role uses the [default
configuration](https://github.com/grafana/agent/blob/main/packaging/grafana-agent.yaml)
and merges custom configuration from the `grafana_agent_config` variable. Refer
to the [Grafana Agent
documentation](https://grafana.com/docs/agent/latest/configuration/) for more
information.
