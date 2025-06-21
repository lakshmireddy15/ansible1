if there are no modules avaialble
1.develop your own module
2.use shell or command line

shell vs Command:
Shell module: If your are using shell module your logging inside the server and ruinning the tasks. It conatin redirects,variabiles...

command module:
executing command from ouside. you will not get any linux full environement redirections piping and variables will not work here


write shell-command.yaml

- name: shell vs command
  hosts: frontend
  tasks:
  - name: redirects ls output to a file
    #ansible.builtin.command: "ls -ltr > /tmp/output.txt"
    ansible.builtin.shell: "ls -ltr > /tmp/output.txt"


Write `inventory.ini` file

We can have any number of nodes.

```ini
[frontend]
<node1-privateIP> ansible_user=ec2-user ansible_password=DevOps321
<node2-privateIP> 

[backend]
<node1-privateIP>
<node2-privateIP>

[local:vars]

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
 
Errors: 
beacause command line redirections are not working

[ ec2-user@ip-172-31-93-59 ~/ansible1 ]$ ansible-playbook -i inventory.ini 21-shell-command.yaml

PLAY [shell vs command] ***************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************
ok: [172.31.85.223]

TASK [redirects ls output to a file] **************************************************************************************************
fatal: [172.31.85.223]: FAILED! => {"changed": true, "cmd": ["ls", "-ltr", ">", "/tmp/output.txt"], "delta": "0:00:00.007431", "end": "2025-06-21 17:10:11.738259", "msg": "non-zero return code", "rc": 2, "start": "2025-06-21 17:10:11.730828", "stderr": "ls: cannot access '>': No such file or directory\nls: cannot access '/tmp/output.txt': No such file or directory", "stderr_lines": ["ls: cannot access '>': No such file or directory", "ls: cannot access '/tmp/output.txt': No such file or directory"], "stdout": "", "stdout_lines": []}

PLAY RECAP ****************************************************************************************************************************
172.31.85.223              : ok=1    changed=0    unreachable=0    failed=1    skipped=0    rescued=0    ignored=0

solution:
[ ec2-user@ip-172-31-93-59 ~/ansible1 ]$ ansible-playbook -i inventory.ini 21-shell-command.yaml

PLAY [shell vs command] ***************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************
ok: [172.31.85.223]

TASK [redirects ls output to a file] **************************************************************************************************
changed: [172.31.85.223]

PLAY RECAP ****************************************************************************************************************************
172.31.85.223              : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

