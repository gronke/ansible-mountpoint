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

### Mounting a 9p virtio shared directory with libvirtd

A libvirt host can share a directory with a guest domain.
```xml
<filesystem type='mount' accessmode='mapped'>
  <source dir='/your/source/path'/>
  <target dir='my_shared_directory'/>
</filesystem>
```

This role can be used to create an fstab entry for this mountpoint
```yaml
- role: gronke.mountpoint
  source: "my_shared_directory"
  opts: "transport=virtio"
  fstype: "9p"
  mountpoint: /media/my_shared_directory
```

