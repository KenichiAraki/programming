### jinja2

##### list variables

example_vars.yml
dhcp"
  neighbors: '["135.121.35.188", "135.121.35.189"]'

example.j2
dhcp:
  neighbors: {{ dhcp.neighbors }}
