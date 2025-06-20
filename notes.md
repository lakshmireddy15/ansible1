How to write Hello World using Ansible playbook

Write hello-world.yaml file 

- name: Hello world
  hosts: local
  connection: local
  tasks:
  - name: Print the Hello world
    ansible.builtin.debug:
    msg: " Hello World"


 Write `inventory.ini` file

We can have any number of nodes.

```ini
[frontend]
<node1-privateIP>
<node2-privateIP>

[backend]
<node1-privateIP>
<node2-privateIP>

[local]
localhost

[database]
<node1-privateIP>
<node2-privateIP>