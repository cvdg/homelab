# cloud-init

- Create Debian 12 VM
  - VM ID: 9000
  - Name: debian12
  - Storage: local
  - ISO: debian-12.8.0-amd64-netinst.iso
  - Qemu agent: true
  - Disk storage: local-lvm
  - Disk size: 32GB
  - CPU socket: 1
  - CPU core: 2
  - Memory: 2048MB
- Boot image and do a graphical install - like  normal
  - Tasksel: SSH server & standard system utilities
  - Reboot
- Login on the console
  - `sudo apt update && sudo apt full-upgrade -y`
  - `sudo apt install cloud-init -y`
  - `sudo cloud-init clean`
  - Shutdown
- 9000 -> Hardware -> Add cloud-init drive (storage: local-lvm)
- 9000 -> Hardware -> Remove CD/DVD
- 9000 -> Cloud-Init -> Edit values -> Regenerate Image
- 9000 -> More -> Convert to template
- Celebrate

## New VM

- 9000 -> More -> Clone
- Name: demo01
- Mode: Full clone
- IPv4/CIDR: 192.168.2.132/24
- Gateway (IPv4): 192.68.2.254
- Regenerate image
- Boot
- Celebrate
