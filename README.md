ansible-mountpoint
==================

Ansible role to create a mountpoint that persists reboots

Examples
--------

### Mounting a disk by UUID
```yaml
- role: gronke.mountpoint
  uuid: 00000000-0000-0000-0000-000000000000
  mountpoint: /var/www
``` 

### Mounting a disk by device path
```yaml
- role: gronke.mountpoint
  source: /dev/sdb1
  mountpoint: /media/other-disk
``` 

### Mounting a loop device
```yaml
- role: gronke.mountpoint
  source: /tmp/diskimage.iso
  opts: ro,loop
  fstype: iso9660
  mountpoint: /media/diskimage

