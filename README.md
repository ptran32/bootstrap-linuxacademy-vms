# bootstrap-linuxacademy-vms

This repo initiate the first configuration for new linuxacademy servers and do these actions below:

- Remove SSH password connection
- Configure private/public key connection
- Install descent linux packages
- Install ohmyzsh as default shell

## Requirements

### Reset default password on all servers

You need to reset the default password on all servers. Use the same password for all servers.

You can find the default password for each server on server playground page.

## Use your own configuration

### Modify inventory

Sometimes after lunch a new server, DNS can take time to propagate. Sometimes primary will come first, sometimes second dns will come first.
Replace 'yourserver' with your server names. You can found it on server playground page.

Modify hosts file:

[primary_dns]  
yourserver321c.mylabserver.com  
yourserver322c.mylabserver.com  
yourserver323c.mylabserver.com  
yourserver324c.mylabserver.com 

[secondary_dns]  
yourserver321d.mylabserver.com  
yourserver322d.mylabserver.com  
yourserver323d.mylabserver.com  
yourserver324d.mylabserver.com

### Modify default variables

Ansible will use the default public key at this location: ~/.ssh/id_rsa.pub

You can change the default location in roles/prepare_linuxacademy_vms/defaults/main.yml

Example:

```
pub_key_location: /home/myuser/.ssh/id_rsa.pub
```

## Usage

Run the command below:

Ansible will ask you for input for ssh password first, and the become pass in second.

```
ansible -i hosts main.yml --ask-pass --ask-become-pass
```
