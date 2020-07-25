# bootstrap-linuxacademy-vms

This repo initiate the first configuration for new linuxacademy servers and do these actions below:

- Remove SSH password connection
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

yourserver321c.mylabserver.com  
yourserver322c.mylabserver.com  
yourserver323c.mylabserver.com  
yourserver324c.mylabserver.com 
```

### Modify default variables

Ansible will use the default public key at this location: ~/.ssh/id_rsa.pub

You can change the default location in roles/prepare_linuxacademy_vms/defaults/main.yml

Example:

```
pub_key_location: /home/myuser/.ssh/id_rsa.pub
```

## Usage

Run the command below:

Ansible will ask you to put your ssh password first, then the become password.

```
ansible -i hosts main.yml --ask-pass --ask-become-pass
```
