Ruby on Rails + Nginx+unicorn + mysql database + Nginx LB: Playbook
-----------------------------------------------------------------------------

- Requires Ansible 2.0
- Expects Ubuntu/Debian distro
- Tested on Linux mint

### Initial Site Setup

Configure the entire stack by listing hosts in the 'hosts'
inventory file, grouped by their purpose:

		[webservers]
		webserver1
		webserver2
		
		[dbservers]
		dbserver
		
		[lbservers]
		lbserver

After which we execute the following command to deploy the site:

		ansible-playbook -i hosts site.yml

The deployment can be verified by accessing the IP address of load
balancer host in a web browser: http://<ip-of-lb>:80. Reloading the page
should have you hit different webservers.

### Removing and Adding a Node

Removal and addition of nodes to the cluster is as simple as editing the
hosts inventory and re-running:

        ansible-playbook -i hosts site.yml

