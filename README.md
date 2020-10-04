# ansible-syslog
Deploy docker container with SYSLOG-server based on pbertera/syslogserver (https://hub.docker.com/)

## Role variables
    Variable                    |       Default value           |      Description
--------------------------------|-------------------------------|---------------------------------------    
syslog_service_name             |       syslog-docker           |   Service name in OS
uninstall_service               |       false                   |
syslog_host_port                |       514                     |   Host network port for service
syslog_container_port           |       514                     |   Container network port for service
syslog_port_type                |       udp                     |   Type of port (tcp/udp) for service
syslog_web_host_port            |       8080                    |   Host network port for management (http)
syslog_web_container_port       |       80                      |   Container network port for management (http)
syslog_web_port_type            |       tcp                     |   Type of port (tcp/udp) for management (http)
docker_image                    |       pbertera/syslogserver   |   Docker image (https://hub.docker.com/)
SYSLOG_USERNAME                 |       none                    |   See below
SYSLOG_PASSWORD                 |       none                    |   See below
---------------------------------------------------------------------------------------------------------

### How to use
    - installation: just start the role
    - uninstallation: add --extra-vars "uninstall_service=true"

#### SYSLOG_USERNAME/SYSLOG_PASSWORD
These variables are used in ./templates/systemd/syslog.service.j2 for web access login/password settings. It's better to store these variables in encrypted file (for example in encrypted <your project ansible directory>/group_vars/all.yml). For more information see - https://docs.ansible.com/ansible/latest/cli/ansible-vault.html