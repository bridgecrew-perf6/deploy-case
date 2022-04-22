# Deploy Case SSH Attempts

Deploy case using ansible and dokcer container.

## Description

This is a project for a case study. The idea was to catch login attempts from alphaclient `(/var/log/auth.log)` either it's success or failed, and send it to alphaserver every 1 minute. The deployment setup automation created using ansible and nodes container using docker.

## Getting Started

### Dependencies

* ansible (versin 2.9.6 or higher)
* python3 (version 3.8.5)
* docker (version 20.10.14)

### Installing

* If you're about to deploy step by step, please start every `ansible-playbook` begin from `preparation` folder and then `setup_nodes` folder.
* Single deployment using `deploy.yaml`
* Please set your host machine at `inventory` 
```
[assignment]
10.10.10.27 #Your machine password

[assignment:vars]
ansible_ssh_user={YOUR_SSH_USERNAME}
#ansible_ssh_password= {YOUR_PASSWORD} #Use this if you are not using ssh keys, but not recommended
```
* Every attempt on alphaclient nodes, will send to alphaserver every minute

### Executing program

* Chain deployment
* Step by step development
```
ansible-playbook -i inventory preparation/install_docker.yaml -K
ansible-playbook -i inventory preparation/pull_image_httpd.yaml
ansible-playbook -i inventory preparation/pull_image_ssh.yaml
ansible-playbook -i inventory setup_nodes/alphaserver/alphaserver.yaml
ansible-playbook -i inventory setup_nodes/alphaclient/alphaclient-1.yaml
ansible-playbook -i inventory setup_nodes/alphaclient/alphaclient-2.yaml
```
* Single deployment
```
ansible-playbook -i inventory deploy.yaml -K
```

### Testing

* Try to access ssh on alphaclient 1 (port 2246) or alphaclient 2 (port 2248) using IP Address from your inventory
```
ssh root@[YOUR_IP_INVENTORY] -p 2246
ssh root@[YOUR_IP_INVENTORY] -p 2248
```

* Web-stat metric for every attempt that happen on alphaclient 1 or alphaclient 2 available through `http://[YOUR_IP_INVENTORY]`
![ScreenShot](/screenshots/hasil.png)


## Help

Any advise for common problems or issues please contact your administrators.

## Authors

Rizky Eka Maulana  
[@rizekamaulana](https://twitter.com/rizekamaulana)

## Version History

* 0.1
    * Initial Release

## Acknowledgments

Inspiration, code snippets, etc.
* [xcad2k](https://github.com/xcad2k/)
* [golinuxcoud](https://www.golinuxcloud.com/)
