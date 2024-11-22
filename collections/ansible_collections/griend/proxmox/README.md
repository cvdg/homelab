# Ansible Collection - griend.proxmox

## bootstrap

Create a user `ansible` and configure `sudo`.

The remote user should have ssh access with a public key or a password to the host to bootstrap the ansible user.

```shell
$ ansible-playbook griend.proxmox.bootstrap -u root -k 
SSH password:

PLAY [Bootstrap a new host with the user ansible] ***********************************************************************************************************

TASK [griend.proxmox.bootstrap : Create group ansible] ******************************************************************************************************
ok: [pve03.griend.dev]

TASK [griend.proxmox.bootstrap : Create user ansible] *******************************************************************************************************
ok: [pve03.griend.dev]

TASK [griend.proxmox.bootstrap : Add ssh authorized key] ****************************************************************************************************
ok: [pve03.griend.dev]

TASK [griend.proxmox.bootstrap : Install sudo] **************************************************************************************************************
ok: [pve03.griend.dev]

TASK [griend.proxmox.bootstrap : Create sudo for user ansible] **********************************************************************************************
ok: [pve03.griend.dev]

PLAY RECAP **************************************************************************************************************************************************
pve03.griend.dev           : ok=5    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

```

Afterwards the user `ansible` should have access as root user.

```shell
$ ansible -m ping all
pve03.griend.dev | SUCCESS => {
    "changed": false,
    "ping": "pong"
}

```

This is not the most complex playbook, but the first one I always run.
