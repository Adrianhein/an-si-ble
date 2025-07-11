## Ansible Ad-Hoc Command

### Inventory file example:

	# Ansible inventory file in 'INI' format
	[First_group]
	192.168.100.20
 	192.168.100.30
 	192.168.100.40

### Format of ad-hoc command usage:
	ansible [pattern] -m [module] -a "[module options]"
 	ansible [inventory entry] -m [module] -a "[module options]"
  
	ansible all -m ping                            ##<< this will output all remote hosts ping result of "First_group"
 	ansible First_group -m command -a "uptime"     ##<< this will output all remote hosts uptime of "First_group"
  	ansible 192.168.100.20 -m command -a "uptime"  ##<< this will output only one remote host's uptime
  
