# Backup

I don't consider files on my workstation - Apple or Linux -
part of my backup. For the same reason I don't consider
Apple iCloud a backup.

I use `rsync` to copy all files in the `~/Documents` folder to
a Linux VM `backup01`.

## 3-2-1 backup rule

- 3 copies of the data
  - `backup01` - VM
  - `nas01` - TrueNAS
  - `usb01` - USB stick
- 2 different media
  - hard disks - `backup01` and `nas01`
  - USB stick - `usb01`
- 1 remote location
  - Proton Drive

## Daily: `backup01` and `nas01`

On the host `backup01` the home-directory is a btrfs.

- `backup01`: I make a snapshot daily.
- `backup01`: I copy with `rsync` the files to a TrueNAS server: `nas01` with
  redundant `zfs` disks.
- `nas01`: A zfs snapshot is made daily.

## Weekly: `usb01` and Proton Drive

- Manually copy my files to a usb stick `usb01`.
- Manually `rclone` my files to Proton Drive.

## To Do

- Automate daily snapshot
- Automate daily sync to `nas01`
- Automate files sync from workstation to `backup01`
