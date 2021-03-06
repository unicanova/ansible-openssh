# Documentation

This role disallow password authentication and disallow root SSH access

+ [Quickstart](#Quickstart)
+ [Example requiremetns.yml file](#Ex1);
+ [Example host file](#Ex2);
+ [Examoke vars/main.yml](#Ex3);

## <a name="Quickstart"></a> Quickstart

[Install ansible](http://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) on the your host
Install python on the servers, if necessary  
You need to create a [requirements.yml](#Ex1) file and write down what roles are required in it. Then install roles from this file.
Install required rolles:  
```sh
$ ansible-galaxy install -r requirements.yml
```
Clone this repository in your directory:

```sh
$ git clone https://github.com/unicanova/ansible-openssh
$ cd ansible-openssh
```
Specify host addresses in the file /etc/ansible/hosts.  
Create a [site.yml](#Ex3) file, which should contain only the title of the role.  

Execute command:  

```sh
$ ansible-playbook site.yml -b --extra-vars "ansible_sudo_pass=yourPassword"
```
#### <a name="Ex1"></a> Example requirements.yml:
```sh
- src: https://github.com/unicanova/ansible-openssh
  version: master
  name: ansible-openssh
```

#### <a name="Ex2"></a> Example hosts file:

```sh
[jenkinsmaster]
192.168.122.123 ansible_ssh_port=22 ansible_ssh_user=ubuntu ansible_ssh_private_key_file=~/.ssh/id_rsa

[jenkinslave]
192.168.122.77 ansible_ssh_port=22 ansible_ssh_user=ubuntu ansible_ssh_private_key_file=~/.ssh/id_rsa
```
#### <a name="Ex3"></a> Example site.yml:
```sh
- hosts: test
  roles:
    - ansible-openssh
```
