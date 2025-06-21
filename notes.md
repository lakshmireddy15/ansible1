How to give variable in the command line

write vars-args.yaml

- name: Varibles from the inventory
  hosts: local
  connection: local
  tasks:
  - name: print variables from the inventory file
    ansible.builtin.debug:
      msg: "My name is {{ NAME }} and my age is {{ AGE }} and my gender is {{ GENDER }}"


Write `inventory.ini` file

We can have any number of nodes.

```ini
[frontend]
<node1-privateIP> 172.31.85.223 NAME= Lakshmi AGE=24 GENDER=Female
<node2-privateIP>

[backend]
<node1-privateIP>
<node2-privateIP>

; [local:vars]

; NAME= Lakshmi
; AGE=24
; GENDER=Female

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
 
 ERROR: we are getting undefined variuable beacuse we commited local variable 

 3.91.62.36 | 172.31.93.59 | t2.micro | https://github.com/lakshmireddy15/ansible1.git
[ ec2-user@ip-172-31-93-59 ~/ansible1 ]$ ansible-playbook -i inventory.ini 11-vars-args.yaml

PLAY [Varibles from the inventory] ****************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************
ok: [localhost]

TASK [print variables from the inventory file] ****************************************************************************************
fatal: [localhost]: FAILED! => {"msg": "The task includes an option with an undefined variable. The error was: 'NAME' is undefined. 'NAME' is undefined\n\nThe error appears to be in '/home/ec2-user/ansible1/11-vars-args.yaml': line 5, column 5, but may\nbe elsewhere in the file depending on the exact syntax problem.\n\nThe offending line appears to be:\n\n  tasks:\n  - name: print variables from the inventory file\n    ^ here\n"}

PLAY RECAP ****************************************************************************************************************************
localhost                  : ok=1    changed=0    unreachable=0    failed=1    skipped=0    rescued=0    ignored=0

solution:
now we can pass aggruments from the command line using -e to pass aggruments

[ ec2-user@ip-172-31-93-59 ~/ansible1 ]$ ansible-playbook -i inventory.ini 11-vars-args.yaml -e "NAME=Lakshmi"  -e "AGE=24"  -e "GENDER=Female"

PLAY [Varibles from the inventory] ****************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************
ok: [localhost]

TASK [print variables from the inventory file] ****************************************************************************************
ok: [localhost] => {
    "msg": "My name is Lakshmi and my age is 24 and my gender is Female"
}

PLAY RECAP ****************************************************************************************************************************
localhost                  : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0


3.91.62.36 | 172.31.93.59 | t2.micro | https://github.com/lakshmireddy15/ansible1.git
[ ec2-user@ip-172-31-93-59 ~/ansible1 ]$


