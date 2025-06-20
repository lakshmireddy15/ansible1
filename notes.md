what is ansible adhoc command?

An Ansible ad-hoc commands is a one line command we can perform simple tasks on remote server without writing ansible playbooks.
It is used when we don't have time

Command:
ansible <inventory.ini> -m <module_name> -a <arruments>
 Parameters:
<host-pattern>: Target hosts from your inventory file (e.g., webservers, all, 192.168.1.10)

-m <module>: Ansible module to use (e.g., ping, shell, yum, copy, command)

-a "<arguments>": Arguments for the module