# Hashicorp-Vault-Ansible
Deploy a production ready [Vault](https://www.vaultproject.io) environment with Ansible

## Setup
1) First, you need to install [Consul](https://www.consul.io/).
__NOTE__: You can use a different storage backend, just be make sure to edit the vaultconfig.hcl files in roles/vaultdeploy/files
2) Edit the hosts file to add in the host you are deploying to.
3) Run the following command: `ansible-playbook deploy.yml -i hosts`
4) Be sure to save all of the keys that get generated by the `Initialize the Vault` step. __THIS IS EXTREMELY IMPORTANT__, if you lose these keys you will not be able to access your vault server. It is reccommended to distribute the keys among people, such that no one person has access to unlocking the entire vault. Keys should be stored with PGP encryption.
5) Once this is finished, you'll need to unseal the vault. Follow the instructions [here](https://www.vaultproject.io/intro/getting-started/deploy.html#seal-unseal). You will need the secrets that you just saved to do this.

At this point, your vault server should be up and running.

## System Requirements
Vault itself will vary in the system requirements needed, but as far as the operating system goes, this playbook has only been tested with Debian Jessie and Centos 7. Presumably, it works on at least Ubuntu 16.04, and potentially Ubuntu 14.04, but both are untested. If anyone has success deploying on a different OS, let me know and I will update this.
