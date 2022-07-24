# ansible-vm-provisioning
Code used by ansible to build VMs in vCenter using RedHat based templates

## Getting started

This code is tested against CentOS Stream, RHEL 8, and RHEL 9.

Perl is required for the VM customization within vCenter. The `Development Tools` group install is recommended which will include all of the required tools.

The account that is used for ansible already needs to be created and have the public key copied into the template being used. The below commands can be used to accomplish this:

```bash
adduser -c "Ansible Service Account" -p $(echo "Password" | openssl passwd -1 -stdin) ansible
echo $'# Grant access to ansible\nansible ALL=(ALL) NOPASSWD: ALL' | EDITOR="tee" visudo -f /etc/sudoers.d/ansible
```

The ssh key for the ansible user can then be copied to the template from the server that has the ssh keys:

```bash
ssh-copy-id <template-server>
```

Then the password can be removed from the ansible user:

```bash
passwd -d ansible
```
