1. Ansible variables
Ansible variables are used to hold some values to used in 
playbooks
They are declared using "{{ var_name }}"
e.g 
ansible-playbook -i inv web.yml -e "target_service=httpd"

2. Ansible facts
* Ansible facts are simple various properties regarding the 
given host
* Ansible facts can be gathered by using "setup" module
ansible host1 -m setup -a "filter=\*ipv4\*"
ansible host1 -m setup -a "filter=\*hostname\*"
* Ansible facts are by default gathered in the playbook
* Facts gathering can be disabled by using "gather_fact: no" in 
  ansible playbook or it can be disabled in "/ect/ansible/ansible.cfg"
* ansible facts can be output to a file by using ansible
	"--tree outputfile" flag 

3. Debugging the ansible
* Ansible can be debuged using "debug" module
  "debug module" has two parameter "msg or var"
* Also "register" module can be used to store the module output 
  and it can be used with the "debug" module  exclusively for 
  more detailed output result of a particular module
* example for debug and "msg"
```
--- 
- host: webserver
  become: yes
  tasks:
  - debug:
      var: target_service # using debug module to see the output 
  - name: Installing a service
    yum: 
      name: "{{ target_service }}"
      state: "latest"
  - name: Making the index.html
    lineinfile: 
	  line: "{{ ansible_hostname }}"
	  path: /var/www/html/index.html
	register: task_debug # Storing the output in "task_debug" register
  - debug:
      msg: " Output of lineinfile is {{ task_debug }}" 
```
4. Handler
* Handler allows to invoke action only when a task performs
  a change.
* No matter how many time handler flagged in plays, it only run's
  during a play's final phase.
* Executing task only once during a change occurs, increases the
  efficiency of plays.
* Handlers can be invoked by "notify" keyword in the playbook
* They may be defined same as task, containing name, module name,
   and listen. 






