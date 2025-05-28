### ansible_facts:

	"ansible_facts" is data or information related to remote systems such as Operating Systems, IP addresses, hostnames, disks, filesystems, users, memory, logs, and etc.

### We can also display ansible facts using ansible ad-hoc command

	ansible managed_hosts -m setup


### We can use grep all information about "ansible_" inside the ansible_facts

	ansible -i "inventory_file" ansible-host-01 -m setup | grep ansible_


### Normal users cannot display complete information of the remote systems

### If we use ansible_facts in playbook, make sure "gather_facts: True"


### Sample ansible_facts playbook

	---
	- hosts: ansible-host-01
  	tasks:
    	- name: Displaying facts variables
      		debug:
        		#msg: "{{ ansible_facts }}"
        		#msg: "{{ ansible_devices }}"
        		#msg: "{{ ansible_devices.vda }}"
        		#msg: "{{ ansible_devices.vda.partitions }}"
        		#msg: "{{ ansible_devices.vda.partitions.vda1 }}"
        		#msg: "{{ ansible_devices.vda.partitions.vda3.size }}"
       			#msg: "{{ ansible_devices['vda']['partitions']['vda3']['size'] }}"
        		msg: "{{ ansible_facts['devices']['vda']['partitions']['vda3']['size'] }}"
	...

### We can use any format, these are same expression:

	msg: "{{ ansible_devices.vda.partitions.vda3.size }}"

	Or

	msg: "{{ ansible_devices['vda']['partitions']['vda3']['size'] }}"

	Or

	msg: "{{ ansible_facts['devices']['vda']['partitions']['vda3']['size'] }}"



### Filtering ansible_facts using "gather_subset="  and "filter="

### " ansible-doc setup " will help more details for "gather_subset" and "filter"

  	ansible -i /root/ansible_tasks/nodes ansible-host-01 -m setup -a "filter=ansible_lvm"  
	ansible -i /root/ansible_tasks/nodes ansible-host-01 -m setup -a "gather_subset=ansible_network"


	
