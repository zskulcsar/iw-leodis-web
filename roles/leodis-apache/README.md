#Leodis-Apache

Installs Apache 2.2.4 on a 12.04 server 


#Requirements

* None

#Role variables

* `apache_group`: www-data
* `apache_user`: www-data
* `apache_installation_dir`: /opt/apache

#Dependencies

None

#Example Playbook


	- name: Leodis webserver provisioning
	  hosts: webserver
	  become: yes
	
	  roles:
		- leodis-apache

#License

BSD

#Author Information

[zskulcsar](https://github.com/zskulcsar)