# Backup

I don't consider files on my workstation - Apple or Linux -
part of my backup. For the same reason I don't consider 
Apple iCloud a backup.

I use `rsync` to copy all files in the `~/Documents` folder to
a Limux VM `backup01`.

## 3-2-1 backup rule

- 3 copies of the data
  - `backup01`
  - `nas01`
  - `usb01`
- 2 different media
  - hard disks
  - usb stick
- 1 remote location
  - Not yet...


## Daily: `backup01` and `nas01`

On the host `backup01` the home-directory is a btrfs.
- `backup01`: I make a snapshot daily.
- `backup01``: I copy with `rsync` the files to a TrueNAS server: `nas01` with
  redundant `zfs` disks.
- `nas01`: A zfs snapshot is made daily.


## Weekly: `usb01`

Manually copy my files to a usb stick `usb01`.


## To Do

- Automate daily snapshot
- Automate daily sync to `nas01`
- Automate files sync from workstation to `backup01`
- Use `rclone` to copy the files to a Proton Drive

