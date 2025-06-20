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


3.91.62.36 | 172.31.93.59 | t2.micro | null
[ ec2-user@ip-172-31-93-59 ~ ]$ cd ansible1

