# playbook

### import playbooks
Only top level in a top level playbook.

```
- hosts: all
  connection: local
  gather_facts: no
  tasks:
    - name: Set environment 
      set_fact:
        version: 1.0

- name: Execute Fabric Builder 'build'
  import_playbook: fabric-builder/build.yml
```


### jinja2

##### list variables

example_vars.yml
dhcp"
  neighbors: '["135.121.35.188", "135.121.35.189"]'

example.j2
dhcp:
  neighbors: {{ dhcp.neighbors }}
