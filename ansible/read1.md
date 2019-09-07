1. Ansible is an automation tool which allows agentless configuration management 
   and deployment 
   Since manual configuring can introduce human error.


2. Ansible inventory 
* Ansible inventory file contains the hosts or a group of targeted host(groups are created by [])
* Ansible default inventory file is present in /ect/ansible/hosts 
* ansible -i customInv // -i flag is used to give the custom ansible inventory file name
* Host can be assign to a variable name using "ansible_host" name:
```
ansiblePort ansible_port=5556
host1 ansible_host=192.168.0.1 
host2 ansible_host=192.168.0.2
[webserver] # A gruop of targeted host named webserver 
web1 ansible_host=192.168.0.3
web2 ansible_host=192.168.0.3
```

3. Ansible modules and documentation 
* modules are specific task to perform on the controller nodes, they are mainly written in python
* We have number of modules for ansible like
file,lineinfile, setup, system, yum, lineinfile,service,  shell and command and many many many more
* For getting the module info we can use ansible-doc 
  ansible-doc -l  # getting all of the modules 
  ansible-doc -s yum # getting documentation of yum module
  

4. Using ansible in AD-HOC mode:
* ad-hoc cmd are similar to bash cmd except it can run on multiple host 
present inventory file. 
* ad-hoc mode is mainly used to test module on targeted host or to do things
  quickly without saving for later 
* In adhoc mode we just execute a single line cmds or more specifically 
modules on our target nodes 

* syntax for ad-hoc mode:
**ansible <HOST> -b -m <module-name> -a "< arg1 arg2 arg3 >"**
e.g: since host1 in present into our ansible inventory file
in "/etc/ansible/hosts"
```
ansible host1 -m ping
ansible host1 -m setup
ansible host1 -b -m yum -a "name=httpd state=latest" 
ansible host1 -b -m service -a "name=httpd state=started"
# -b flag means become a su to install the package
ansible host1 -b -m yum -a "name=httpd state=absent" # It will going to insinstal the httpd service
```
* If we run the same  module again and again on the host, there will be no change on host since the desired 
state is already achieved.

* However shell and command are exceptional module.


6. Ansible playbooks

* More like a bash script containing a list of cmds 
* As ansible ad-hoc cmds are run using "ansible" keyword,where as ansible playbook 
are invoked using "ansible-playbook *playbookfile*"
* Ansible palybooks are written in yaml.
* Playbooks contains different element called plays(series of steps to run on hosts) which atleast contains 
	one host and one task.
* Each task in turns contains task name and module name and its the module parameter.
* Example for a playbook:
```
web.yml 
---  #comments 
- host: webserver
  become: yes # run the below task with the sudo priveledge 
  task: 
  - name: latest httpd installation
    yum: # module name 
      name: httpd # parameter for yum module 
      state: latest
  - name: service httpd start
  	service: # start the service with service module 
  	  name: httpd
  	  state: started # Defining the state of the service module
```

* ansible-playbook -i inv web.yml 
* ansible -i inv1 web.yml --check # --check flag can be used to dry-run the ansible playbook
* If a playbook fails it generates a **retry file** for that playbook which can be run later




