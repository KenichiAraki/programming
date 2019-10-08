# playbook

### import playbooks
Only top level in a top level playbook.

```
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
