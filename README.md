notes-openstack
===============

#### Install QEMU (With KVM Functionalities)
```sh
sudo apt-get install qemu-system qemu-utils qemu-kvm libvirt-bin
```

#### Create an Virtual Drive with QEMU
```sh
qemu-img create -f qcow2 <image_name>.qcow2 10G
```

### Create Script
```sh
#!/bin/bash

#### Configuration #####
#
QEMU_KVM='qemu-system-x86_64'
CPUs="cores=4,threads=1,socket=1"
RAM=1024
CLOCK_BASE="utc"
#
########################


if [ $# -lt 2 ]; then
cat <<EOF
Usage: $0 drive cdrom

    drive       Virtual drive where the system will be installed
    cdrom       ISO installer of the operating system

EOF
    exit 1
fi

bin_qemu_kvm=`which $QEMU_KVM | wc -l`
if [ "$bin_qemu_kvm" == "0" ]; then
    echo "The program $QEMU_KVM cannot be found"
    exit 1
fi

if [ ! -f "$1" ]; then
    echo "The virtual drive file $QEMU_KVM doesn't exist"
    exit 1
fi

if [ ! -f "$2" ]; then
    echo "The ISO installer $QEMU_KVM doesn't exist"
    exit 1
fi

$QEMU_KVM \
        -nodefaults \
        -drive file=$1,if=virtio,id=drive-virtiodisk0,cache=none \
        -cdrom $2 \
        -boot once=d,menu=on \
        -enable-kvm \
        -cpu host \
        -smp $CPUs \
        -m $RAM \
        -rtc base=$CLOCK_BASE,clock=host \
        -netdev user,id=usernet,net=169.254.0.0/16,hostfwd=tcp::2222-:22,hostfwd=tcp::8080-:80 \
        -device virtio-net-pci,netdev=usernet \
        -vga cirrus
```
### Execute
```sh
chmod +x qemu-install
./qemu-install debian-7-32.qcow2 debian-7.5.0-i386-netinst.iso
```

#### Convert an Image with QEMU
```sh
# Convert from vdi to qcow2
qemu-img convert -f vdi -O qcow2 ubuntu.vdi ubuntu.qcow2
```

#### Nova Commands
```sh
nova list # List Servers

```

#### Neutron Commands
```sh
neutron net-list # List Networks
```

--
<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons Licence" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">notes-openstack</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://jim-beaudoin.com" property="cc:attributionName" rel="cc:attributionURL">Jimmy Beaudoin</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
