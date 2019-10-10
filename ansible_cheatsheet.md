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
- an inventory file (e.g. 'hosts' or -i "host,") are preprocessed, 
thus an inventory file cannot be overriden for an imported playbook; 
e.g. fabric-builder/hosts.
- facts (by set_facts) are used in an imported playbook as well as vars.
- playbook/host_vars nor group_vars are read during import.


### jinja2

##### list variables

example_vars.yml
dhcp"
  neighbors: '["135.121.35.188", "135.121.35.189"]'

example.j2
dhcp:
  neighbors: {{ dhcp.neighbors }}


##### templates tips

Dictionary

python 3
{% for key, value in dhcp_server.options.items() %}
option {{ key }} {{ value }};
{% endfor %}

python 2
{% for key, value in dhcp_server.options.iteritems() %}
option {{ key }} {{ value }};
{% endfor %}
