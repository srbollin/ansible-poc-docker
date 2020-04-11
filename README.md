# ansible-poc-docker
#Tested with RHEL 7 (Disable SE Linux) and ansible 2.9.6

#Run below command to deploy ELK stack
#ansible-playbook -i hosts deploy_poc_stack.yml --tags "elk"

#Run below command to deploy MySQL, PHP, Redis, NGNIX
#ansible-playbook -i hosts deploy_poc_stack.yml --tags "fullstack"
