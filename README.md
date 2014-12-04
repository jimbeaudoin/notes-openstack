openstack-notes
===============

#### Install QEMU
```sh
sudo apt-get install qemu-system qemu-utils
```

#### Create an Image with QEMU
```sh
qemu-img create -f qcow2 <image_name>.qcow2 10G
```

#### Convert an Image with QEMU
```sh
# Convert from vdi to qcow2
qemu-img convert -f vdi -O qcow2 ubuntu.vdi ubuntu.qcow2
```
