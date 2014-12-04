openstack-notes
===============

#### Convert Image with QEMU
```sh
# Convert from vdi to qcow2
qemu-img convert -f vdi -O qcow2 ubuntu.vdi ubuntu.qcow2
```
