## Ansible Practicals

<p align="center">
 <img src="images/logo.png?raw=true" alt="Ansible Practicals Logo" width="30%" height="20%" />
</p>

## Ansible Architecture
![Ansible Architecture](https://www.kreyman.de/images/Sonstige/Ansible/Ansible_Architecture_Diagram.png)

### What is Ansible?

 Ansible is an open source software provisioning, configuration management an application-deployment 
tool enabling infrastructure as code. It runs on many Unix-like systems, and can configure both Unix-like systems as well as Microsoft Windows

Ansible aims to be:
1. Clear - Ansible uses a simple syntax (YAML) and is easy for anyone (developers, sysadmins,
managers) to understand. APIs are simple and sensible.
2. Fast - Fast to learn, fast to set up, especially considering you don’t need to install extra agents
or daemons on all your servers!
3. Complete - Ansible does three things in one, and does them very well. Ansible’s ‘batteries
included’ approach means you have everything you need in one complete package.
4. Efficient - No extra software on your servers means more resources for your applications.
Also, since Ansible modules work via JSON, Ansible is extensible with modules written in a
programming language you already know.
5. Secure - Ansible uses SSH, and requires no extra open ports or potentially-vulnerable daemons
on your servers.

For this demo, we will be using two Ubuntu 22.04 LTS virtual box machine

## Installing Ansible
## Ansible Lab Set Up with Oracle VirtualBox
- sudo apt remove ansible
- sudo apt update
- sudo apt install software-properties-common
- sudo apt install ansible
- ansible--version

_now you can get the ansible configuration location_


```ssh-keygen```
```ssh-copy-id -i /home/your dir/.ssh/id_rsa.pub user@ip address```


## Creating a basic inventory file
- Ansible uses an inventory file (basically, a list of servers) to communicate with your servers. Like
a hosts file (at /etc/hosts) that matches IP addresses to domain names, an Ansible inventory file
matches servers (IP addresses or domain names) to groups
- Default ansible file path
_/etc/ansible/hosts_
<p align="left">
<img src="images/v1.png" alt="" />
</p>

###  Running your first Ad-Hoc Ansible command

An ad-hoc command consists of two parameters: The host group that defines on what machines to run the task against and the Ansible module to run.

_ ansible testserver -m ping_
<p align="left">
<img src="images/v2.png" alt="" />
</p>
 _ansible testserver -a 'uptime'_
<p align="left">
<img src="images/v3.png" alt="" />
</p>
_ ansible testserver -m command -a 'df -h'_
<p align="left">
<img src="images/v4.png" alt=""  />
</p>
_ ansible testserver -m command -a 'ls -l'_
<p align="left">
<img src="images/v5.png" alt=""  />
</p>


## Ansible Facts with Labs (Learning about your environment)
- The setup module and how this relates to fact gathering
- Filtering for specific facts
- The creation/execution of custom facts
- How custom fact can be used in environment without super access

 ansible testserver -m setup
<p align="left">
<img src="images/v6.png" alt=""  />
</p>
 _ansible testserver -m setup -a 'gather_subset=network'| more_
<p align="left">
<img src="images/v7.png" alt=""  />
</p>
_ ansible testserver -m setup -a 'filter=ansible_mem*'_
<p align="left">
<img src="images/v8.png" alt=""  />
</p>
 _ansible testserver -m setup -a 'filter=ansible_memtotal_mb'_
<p align="left">
<img src="images/v9.png" alt=""  />
</p>


## Your first Ansible playbook
_cat facts_playbook.yml_
<p align="left">
<img src="images/v10.png" alt=""  />
</p>


_sudo vi facts.d_
_bash facts.d_

## Ansible Register and When to use
_cat register_playbook.yml_
<p align="left">
<img src="images/v11.png" alt=""  />
</p>

_ansible-playbook register_playbook.yml_

_cat register2_playbook.yml_
<p align="left">
<img src="images/v12.png" alt=""  />
</p>



## Ansible Playbook and Dynamic Facts with Labs
_cat fact3_playbook.yml_
<p align="left">
<img src="images/v13.png" alt=""  />
</p>



## Run Ansible commands Asynchronous & Parallel
- Playbook perfomance and bottleneck polling
- Asynchronous job identifiers
- Asynchronous status handling
- Serial execution
- Batch execution
- Alternative execution strategies

_sudo vi slow_playbook.yml_

_time ansible-playbook slow_playbook.yml_



## Ansible Include, Import & Tags
_sudo vi include_playbook.yml_
_cat play1_task2.yml_

## Difference between static and dynamic include/import approaches
_Recommendation for choosing approach_

```  include_tasks=Dynamic```
```include=static by default, can be dynamic```
```import_task=static```

```include=depreceated```
``` include_task=*dynamic , can be used in loops```
```import=static , cannot be used with loops```



## Ansible Roles 
- Ansible roles are a way to group multiple task together into container to do the automation in very effective mannner with clean directory str
ucture.
-  Roles are the set of task and additional files for alternation roles which allows you break up the configuration
- Allows reuse of code by anyone
- Reduce the syntax error
- Allow one to create a directory structure 

### How to Create a role
_ansible-galaxy init /etc/ansible/roles/http_

### How to Remove a role
_ansible-galaxy remove /etc/ansible/roles/_

```ansible-galaxy init role_name``` - Running this command creates an example role in
the current working directory, which you can modify to suit your needs. Using the init
command also ensures the role is structured correctly in case you want to someday
contribute the role to Ansible Galaxy

### Other role parts: handlers, files, and templates


## Ansible Vault
Ansible vault is a feature of ansible that allows you to keep sensitive data such as password or encrypted
file rather than as plain text or values

1. Create: To create ansible vault file in the encrypted file
View: To view data in the ecrypted file
2. Edit: To edit ecrypted file
3. Encrypt: To encrypt unecrypted file
4. Decrypt: To decrypt an ecrypted file
5. --ask-vault-pass: to provide password
6. --vault-password file: to pass a vault passowrd through a file* 

 _ansible-vault create vault Testing_playbook.yml_

## License

Shield: [![CC BY-NC-SA 4.0][cc-by-nc-sa-shield]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg
