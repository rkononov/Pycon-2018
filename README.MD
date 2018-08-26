# Ansible

## Installing

### Ubuntu

```bash
$ sudo apt-get update
$ sudo apt-get install software-properties-common
$ sudo apt-add-repository ppa:ansible/ansible
$ sudo apt-get update
$ sudo apt-get install ansible
```

### MacOS

http://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html?#latest-releases-via-pip

### Pip

```bash
$ sudo pip install ansible
```

## How to use

### Update list of hosts

Edit config/hosts.ansible file, configure list of servers you watn to operate (ip addresses, names)

### Install docker & docker-compose on node

```bash
 ansible-playbook library/install_docker.yml
```

### Install/Update configs/restart geth on node

Dry run without any changes (but it will show you the changes) on node5 (list of available hosts is in hosts.ansible file)

```bash
  ansible-playbook --limit=gethnode5 node.yml --diff --check
```

Applying changes to selected host (node5)

```bash
  ansible-playbook --limit=gethnode5 node.yml --diff
```

Or if you want to update all devnodes

```bash
  ansible-playbook --limit=gethnodes node.yml --diff --check
```


### Updating/changing configuration scripts

Configs are stored in config/gethnet.yml file (config/vars.yaml are for docker/docker-compose installation and hosts.ansible just list of hosts)
Templates are stored in templates folder (docker-compose.yaml and config)

Node folder contains static files that should be just copied to node instance without changing.