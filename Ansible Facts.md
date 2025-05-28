### ansible_facts:

	"ansible_facts" is data or information related to remote systems such as Operating Systems, IP addresses, hostnames, disks, filesystems, users, memory, logs, and etc.

### We can also display ansible facts using ansible ad-hoc command

	ansible managed_hosts -m setup

### Normal users cannot display complete information of the remote systems

### If we use ansible_facts in playbook, make sure "gather_facts: True"

	
