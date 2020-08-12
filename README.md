# bootstrap-linuxacademy-vms

This repo initiate the first configuration for new linuxacademy centos servers and do these actions below:

- Remove SSH password connection
- Add cloud_user as sudoers
- Configure private/public key connection
- Install descent linux packages
- Install ohmyzsh as default shell

## Requirements

### Reset default password on all servers

You need to manually reset the default password provided by linuxacademy on each new server. Use the same password for all servers.

## Use your own configuration

### Modify inventory

Modify hosts file by replacing 'yourserver' with the corresponding DNS. You can found them on cloud playground section.

```
[lac-servers]  

yourserver1c.mylabserver.com  
yourserver2c.mylabserver.com  
yourserver3c.mylabserver.com  
yourserver4c.mylabserver.com 
```

### Modify default variables

Ansible will use the default public key at this location: ~/.ssh/id_rsa.pub

You can change the default location in roles/prepare_linuxacademy_vms/defaults/main.yml

Example:

```
pub_key_location: /home/myuser/.ssh/id_rsa.pub
```

## Usage

Run the command below to bootstrap new VM's:

Ansible will ask you to put your ssh password first, then the become password.

```
ansible-playbook -i hosts main.yml --ask-pass --ask-become-pass
```

Install common package task take some times because of yum install

Future connections will now use cloud_user and your private/public key.
