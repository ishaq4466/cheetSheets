
Ansible inventory  contains the hosts or a group of targeted host
ansiblePort ansible_port=5556

host1 ansible_host=192.168.0.1
host2 ansible_host=192.168.0.2
[webserver]
web1 ansible_host=192.168.0.3
web2 ansible_host=192.168.0.3


4. Ansible modules and documentation 
modules are specific task to perform on the controller nodes

ansible-doc -l  getting all of the modules 
ansible-doc -s yum getting documentation of yum module

file, system, yum, lineinfile,service,  shell and command and many many many more

5. Using ansible in AD-HOC mode:
* ad-hoc cmd are similar to bash cmd except it can run on multiple host 
present inventory 


*In adhoc mode we just execute a single line cmds or more specifically 
modules on our target nodes 
syntax for ad-hoc mode:
ansible <HOST> -b -m <module-name> -a "<arg1 arg2 arg3>"
e.g: since host1 in present into our ansible inventory file
in "/etc/ansible/hosts"
ansible host1 -m ping
ansible host1 -m setup
ansible host1 -b -m yum -a "name=httpd state=latest" 
//-b flag means become a su to install the package
ansible host1 -b -m service -a "name=httpd state=started"
*if we run the same above cmd there will be no change since the desired 
state is already achieved.

*shell and command are exceptional

6. Ansible playbook 

* More like a bash script containing a list of cmds 
* As ansible ad-hoc cmds are run using "ansible" keyword, ansible playbook 
are invoked using "ansible-playbook playbookfile"
* Ansible palybooks are written in yaml.
* Playbooks contains different element called plays(series of steps to run on hosts) which atleast contains 
	one host and one task
* Each task in turns contains task name and module name and its the module parameter.

web.yml 
--- #comments 
- host: webserver
  become: yes # run the below task with the sudo priveledge 
  task: 
  - name: latest httpd installation
    yum: # service name 
      name: httpd
      state: latest
  -name:
   file
  - name: service httpd start
  	service: # start the service with service module 
  	  name: httpd
  	  state: started



ansible-playbook -i inv web.yml --check  # to specify different ansible inventory file

if a playbook fails it generates a retry file for that playbook which 
can be run later
