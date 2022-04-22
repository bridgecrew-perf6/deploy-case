# Project Title

Deploy case using ansible and dokcer container.

## Description

This is a project for a case study.

## Getting Started

### Dependencies

* ansible (versin 2.9.6 or higher)
* python3 (version 3.8.5)
* docker (version 20.10.14)

### Installing

* If you're about to deploy step by step, please start every `ansible-playbook` begin from `preparation` folder and then `setup_nodes` folder.
* Single deployment using `deploy.yaml`
* Please set your host machine at `inventory` 

### Executing program

* Chain deployment
* Step-by-step bullets
```
ansible-playbook -i inventory preparation/install_docker.yaml -K
```
```
ansible-playbook -i inventory preparation/pull_image_httpd.yaml
```
```
ansible-playbook -i inventory preparation/pull_image_ssh.yaml
```
```
ansible-playbook -i inventory setup_nodes/alphaserver/alphaserver.yaml
```
```
ansible-playbook -i inventory setup_nodes/alphaclient/alphaclient-1.yaml
```
```
ansible-playbook -i inventory setup_nodes/alphaclient/alphaclient-2.yaml
```
* Single deployment
```
ansible-playbook -i inventory deploy.yaml -K
```

## Help

Any advise for common problems or issues please contact your administrators.

## Authors

Contributors names and contact info

Rizky Maulana  
[@rizekamaulana](https://twitter.com/rizekamaulana)

## Version History

* 0.1
    * Initial Release

## Acknowledgments

Inspiration, code snippets, etc.
* [xcad2k](https://github.com/xcad2k/)
* [golinuxcoud](https://www.golinuxcloud.com/)