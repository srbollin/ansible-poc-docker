# ansible-poc-docker
#Tested with RHEL 7 (Disable SE Linux) and ansible 2.9.6

#Run below command to deploy ELK stack


ansible-playbook -i hosts deploy_poc_stack.yml --tags "elk"




#Run below command to deploy MySQL, PHP, Redis, NGNIX


ansible-playbook -i hosts deploy_poc_stack.yml --tags "fullstack"



#Deploy Filebeat using below command


ansible-playbook -i hosts -t filebeat deploy_elk_stack.yml

### Filebeat

Filebeat is not installed in a Docker container to add flexibility for making changes in its configuration.

Filebeat configuration is in /etc/filebeat/filebeat.yml. once is installed in the server add the ngnix logs path as shown below.

A prospector to send server logs has been configured:

	- type: log
	  enabled: true
	  paths:
		- /var/log/*.log
    		- /var/log/ngnix/*.log
		
Which then sends all the existing and new logs to Logstash:

Execute Filebeat with the command: 

	sudo filebeat
	 
### Kibana

Access to Kibana using http://[ELK-SERVER]:5601.

Under Management/Index Patterns the new index is found (my_index_1) and a new index pattern can be created. 

All the messages will be then available in the Discover section.
