Create Ec2 instance

Ec2 ---> instances ---> lanuch instances ---> <server_name> ------Application and OS Images = go to browse more AMI's --> Community AMI's ----> search ----> devops-practice ---wait for few min --> select (RHEL-9-DevOps-Practice)
instance type =t2.micro
key pair ---> without using key pair
sercurity ----> select your security gruop --> lanch

create 3 instances
Ansible-server
node1
node2

paste nodes private ip's in the inventory.ini file.
We can use one node can be in multiple groups
Bash:
git clone https://github.com/lakshmireddy15/ansible1.git

Mobaxterm: ansible-server
sudo dnf install ansible -y 
git clone https://github.com/lakshmireddy15/ansible1.git
output:
git clone https://github.com/lakshmireddy15/ansible1.git
Cloning into 'ansible1'...
remote: Enumerating objects: 47, done.
remote: Counting objects: 100% (47/47), done.
remote: Compressing objects: 100% (36/36), done.
remote: Total 47 (delta 21), reused 36 (delta 10), pack-reused 0 (from 0)
Receiving objects: 100% (47/47), 4.64 KiB | 2.32 MiB/s, done.
Resolving deltas: 100% (21/21), done.


54.210.227.178 | 172.31.22.186 | t2.micro | null
[ ec2-user@ip-172-31-22-186 ~ ]$ cd ansible1

54.210.227.178 | 172.31.22.186 | t2.micro | https://github.com/lakshmireddy15/ansible1.git
[ ec2-user@ip-172-31-22-186 ~/ansible1 ]$

Write playbook.yaml file

# ping the server
- name: ping the sever
  hosts: local
  connection: local
  tasks:
  - name: ping the server
    ansible.builtin.ping:






