### first set relationship in the software
- settings —— shared folder —— add(shared-D:\SharedFolder )—— auto mount / fixed allocation / confirm

### install dependencies
- yum install -y kernel-devel gcc

### mount the ISO and do install
- mount /dev/cdrom /mnt/cdrom
- cd /mnt/cdrom ./VBoxLinuxAdditions.run

### mount share folder
- mkdir /mnt/shared
- mount -t vboxsf shared /mnt/shared

finished