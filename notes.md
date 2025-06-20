How to write multiple plays in a playbook

write multi-plays.yaml

- name: Play1
  hosts: local
  connection: local
  tasks:
  - name: Task 1 and play 1
    msg: " This is Task 1 and Play 1"
  - name: Task 1 and play 2
    msg: " This is Task 1 and Play 2"

- name: Play2
  hosts: local
  connection: local
  tasks:
  - name: Task 2 and play 1
    msg: " This is Task 2 and Play 1"
  - name: Task 2 and play 2
    msg: " This is Task 2 and Play 2"

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



Initial Setup on Ansible-server
Bash:

git clone https://github.com/lakshmireddy15/ansible1.git

DELL@DESKTOP-LNC7QP1 MINGW64 ~/Documents/DevOps/DevOps_Projects/repos
$ cd ansible1

DELL@DESKTOP-LNC7QP1 MINGW64 ~/Documents/DevOps/DevOps_Projects/repos/ansible1 (main)
$ git add . ; git commit -m "ansible" ; git push origin main
[main 67aa0f5] ansible
 3 files changed, 34 insertions(+), 52 deletions(-)
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 4 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 755 bytes | 755.00 KiB/s, done.
Total 5 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/lakshmireddy15/ansible1.git
   dbd2cae..67aa0f5  main -> main


Mobaxterm (on Ansible-server):

sudo dnf install ansible -y 
git clone https://github.com/lakshmireddy15/ansible1.git


Output:

git clone https://github.com/lakshmireddy15/ansible1.git
Cloning into 'ansible1'...
remote: Enumerating objects: 47, done.
remote: Counting objects: 100% (47/47), done.
remote: Compressing objects: 100% (36/36), done.
remote: Total 47 (delta 21), reused 36 (delta 10), pack-reused 0 (from 0)
Receiving objects: 100% (47/47), 4.64 KiB | 2.32 MiB/s, done.
Resolving deltas: 100% (21/21), done.
```54.210.227.178 | 172.31.22.186 | t2.micro | null`
`[ ec2-user@ip-172-31-22-186 ~ ]$ cd ansible1`

`54.210.227.178 | 172.31.22.186 | t2.micro | https://github.com/lakshmireddy15/ansible1.git`
`[ ec2-user@ip-172-31-22-186 ~/ansible1 ]$`

[ ec2-user@ip-172-31-93-59 ~/ansible1 ]$ git pull
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 5 (delta 3), reused 5 (delta 3), pack-reused 0 (from 0)
Unpacking objects: 100% (5/5), 715 bytes | 715.00 KiB/s, done.
From https://github.com/lakshmireddy15/ansible1
   cac1c26..5e5b843  main       -> origin/main
Updating cac1c26..5e5b843
Fast-forward
 03-install.yaml |  9 ++++-----
 inventory.ini   |  2 +-
 notes.md        | 91 +++++++++----------------------------------------------------------------------------
 3 files changed, 14 insertions(+), 88 deletions(-)

[ ec2-user@ip-172-31-93-59 ~/ansible1 ]$ ansible-playbook -i inventory.ini -e ansible_user=ec2-user -e ansible_password=DevOps321 04-multi-plays.yaml
ERROR! this task 'msg' has extra params, which is only allowed in the following modules: ansible.builtin.script, ansible.legacy.import_role, ansible.windows.win_command, raw, ansible.legacy.group_by, ansible.legacy.script, ansible.builtin.win_command, win_shell, ansible.legacy.raw, ansible.builtin.add_host, group_by, ansible.builtin.meta, ansible.builtin.win_shell, ansible.builtin.shell, ansible.builtin.include, ansible.legacy.import_tasks, add_host, ansible.legacy.include_role, include_vars, ansible.legacy.win_command, meta, include, import_tasks, ansible.legacy.command, ansible.builtin.include_tasks, ansible.legacy.shell, ansible.windows.win_shell, ansible.legacy.include, ansible.legacy.include_tasks, ansible.builtin.raw, ansible.builtin.command, ansible.builtin.import_tasks, ansible.legacy.add_host, ansible.legacy.include_vars, command, ansible.legacy.win_shell, win_command, import_role, ansible.legacy.meta, script, include_role, set_fact, ansible.builtin.group_by, shell, ansible.builtin.include_vars, ansible.legacy.set_fact, include_tasks, ansible.builtin.include_role, ansible.builtin.set_fact, ansible.builtin.import_role

The error appears to be in '/home/ec2-user/ansible1/04-multi-plays.yaml': line 5, column 5, but may
be elsewhere in the file depending on the exact syntax problem.

The offending line appears to be:

  tasks:
  - name: Task 1 and play 1
    ^ here


ERROR:

Here i forgot to mention ansible builtin funtion to prit the output

below is the tatest file:

- name: Play1
  hosts: local
  connection: local
  tasks:
  - name: Task 1 and play 1
    ansible.builtin.debug:
      msg: " This is Task 1 and Play 1"
  - name: Task 1 and play 2
    ansible.builtin.debug:
      msg: " This is Task 1 and Play 2"

- name: Play2
  hosts: local
  connection: local
  tasks:
  - name: Task 2 and play 1
    ansible.builtin.debug:
      msg: " This is Task 2 and Play 1"
  - name: Task 2 and play 2
    ansible.builtin.debug:
      msg: " This is Task 2 and Play 2"

Note: After doing any changes in file we need to do git add and git pull same like above
$ git add . ; git commit -m "ansible" ; git push origin main
mobaxterM:
git pull
ansible-playbook -i inventory.ini -e ansible_user=ec2-user -e ansible_password=DevOps321 04-multi-plays.yaml


PLAY [Play1] ***********************************************************************************************

TASK [Gathering Facts] *************************************************************************************
ok: [localhost]

TASK [Task 1 and play 1] ***********************************************************************************
ok: [localhost] => {
    "msg": " This is Task 1 and Play 1"
}

TASK [Task 1 and play 2] ***********************************************************************************
ok: [localhost] => {
    "msg": " This is Task 1 and Play 2"
}

PLAY [Play2] ***********************************************************************************************

TASK [Gathering Facts] *************************************************************************************
ok: [localhost]

TASK [Task 2 and play 1] ***********************************************************************************
ok: [localhost] => {
    "msg": " This is Task 2 and Play 1"
}

TASK [Task 2 and play 2] ***********************************************************************************
ok: [localhost] => {
    "msg": " This is Task 2 and Play 2"
}

PLAY RECAP *************************************************************************************************
localhost                  : ok=6    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

