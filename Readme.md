## Leodis webserver management

As per the description an Ansible role is presented here what can be run on either provisioned or unprovisioned servers.
The main issues highlihted below.

### Assumptions
* All the webservers in the Leodis deployment are configured the same
* It is assumed that apache configuration is deliberately wrong (ie.: not able to server HTTP status pages) - normally this should be brought up with the sys admin team

### Issues with the current install
* Apache is deployed into a non-standard location :: this is left untouched but parameter has been added to the role
* Apache is not deployed via the common repositories available :: left untouched. the leodis-apache role uses a binary created from the original installation
* No dedicated user for apache :: the role creates the predefined user
* The deployment is owned by root :: the apache config has been modified to use the preconfigured user (parameter driven)
* Apache is being run as root :: the apache config has been modified to use the preconfigured user (parameter driven)
* No log rotations is specified for the access / error_log :: not part of the role, suggestion for the ops team would be to extend with this 

### Usage
You must have Ansible 2.1 installed. [Ansible Installation](http://docs.ansible.com/ansible/intro_installation.html)
You must have the appropriate SSH private key file in hand.
You must know public IP addresses for the server to be managed.

* Please update the ansible.cfg file and
    * change the "private_key_file" to point to the private key file
    * change the "remote_user" as required
* Please update the "leodis.inventory" file and include the public IP addresses of the servers to be managed
* Run the playbook with command "ansible-playbook site.yml -v"

Any subsequent re-run will update the server as per Ansible's principals.

Any modifications required in the apache configuration can be done in the "roles/leodis-apache/templates" folder.

Notes:
* it is adviseable to add the server fingerprints to the known hosts list if not already there 

### TODO
* Logrotation as above
* Better inventory management (this should be based on the client needs)